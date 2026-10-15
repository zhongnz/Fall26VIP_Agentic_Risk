# τ²-bench retail development runs (Pair case #58)

Both notebooks run [τ²-bench](https://github.com/sierra-research/tau2-bench) at commit
`5bfa7e37b366` (retail domain) in Google Colab, reading a Gemini API key from Colab
secrets. They are **development evidence**: they check that the setup works and look
for failures. They do not estimate a failure rate and do not test the completeness check.

| Notebook | Date (ET) | Task selector | Task IDs | Trials | Outcome |
| --- | --- | --- | --- | --- | --- |
| [`tau2_retail_baseline.ipynb`](tau2_retail_baseline.ipynb) | 2026-10-07 | Two or more expected state-changing tool calls (44 of 114 tasks); first five by ID | 4, 11, 14, 16, 22 | 1 | 5/5 solved, assembled from four attempts (below) |
| [`tau2_retail_pilot.ipynb`](tau2_retail_pilot.ipynb) | 2026-10-07 | Reference solution changes two or more items; one call that changes two items counts as two (59 of 114 tasks); first ten by ID | 0, 2, 4, 11, 13, 14, 16, 20, 21, 22 | 4 | 39/40 solved; all four trials solved in 9/10 tasks; 0 infrastructure errors |

The two selectors differ: a single exchange or return call on two items counts once
under the first and twice under the second (task 0 is selected only by the second).

## Shared settings and deviations

- Agent, simulated customer and natural-language judge: `gemini/gemini-3.8-flash` through LiteLLM.
- **Judge deviation:** τ²-bench's default judge for "tell the user X" checks is OpenAI
  `gpt-4.1`. The notebooks patch it to the same Gemini model, ask for plain JSON, and strip a
  code fence before parsing.
- Seed 300 (τ²-bench default). Concurrency 1 (baseline) and 4 (pilot).
- Error output is filtered so that API keys in request URLs are masked.
- Cost and size (pilot): about 1 minute, 101K input tokens, 4.7K output tokens and $0.09 per
  run for the agent and simulated customer (judge excluded).

## First run: attempts and infrastructure failures

The five-task result combines four attempts on 2026-10-07 (UTC timestamps in file names).
Every non-solved outcome was an infrastructure error; no attempt produced a task failure.

| Attempt (UTC) | Solved | Infrastructure errors |
| --- | --- | --- |
| 04:52 | 11, 14, 22 | 4, 16 — default judge required an OpenAI key (led to the judge patch) |
| 10:56 | 11, 14, 22 | 4, 16 — judge JSON wrapped in a code fence (led to fence stripping) |
| 11:43 | 4, 11 | 14, 16, 22 — prepaid API credit ran out (HTTP 402) |
| 11:57 | 16 (run alone) | — |

Only tasks 4 and 16 have "tell the user X" checks, so the judge fixes did not affect the
earlier results for tasks 11, 14 and 22.

## Pilot: plan, failure review and labels

- The plan and decision rule were posted in [#62](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/62#issuecomment-6049640445) before running.
- The single failure (task 4) came from the simulated customer, who asked about only one of
  two pending orders; in the passing trials the customer asked for all orders. It is a
  simulator issue, not an agent omission ([trace review](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/62#issuecomment-6183015987)).
- The notebook's `missing_writes` column uses exact matching against the reference tool
  calls. It only flags candidate failures: equivalent calls can still reach the correct state,
  so each label must be checked against the required final state and the trace.
- On 2026-10-14 the pilot notebook's printed labels and summary field were renamed from
  "missed-change failures" to "candidate failures" after the trace review. The computation is
  unchanged; the run itself printed "1 missed-change failure → borderline" under the old labels.

## Run files

Full results and summaries are kept locally (`results/local/tau2-retail/`, not committed)
and can be shared on request. SHA-256:

| File | SHA-256 |
| --- | --- |
| `results-baseline-20261007-045210.json` | `a7e1ebbf83574fcca1bbb7fc633de19da0dd7f9bdd1e266f609f88f1402365e4` |
| `results-baseline-20261007-105629.json` | `c1458d1d548399520250a01f13bf9dfd479c566e46836c25dda47cbc26840711` |
| `results-baseline-20261007-114331.json` | `6a7de4e0ecb6fb4c833336e444c0df4f2670a1904bad073589b142b7cdfb3b27` |
| `results-baseline-20261007-115707.json` | `9e7b38c76468d0b9b1b1eba152f329e9d4a63753789013993b481e6593c3470b` |
| `results-pilot-20261008-003929.json` | `7c18b024c806ecd02104c658f0278eede42ee91a6af32ede8c1aff6984844667` |
| `summary-pilot-20261008-003929.json` | `ad3b6204160e068d55ab262d7080450bd7561f6589ac519387866baa5f517283` |
