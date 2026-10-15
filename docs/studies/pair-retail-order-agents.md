# Pair case — Verification failures in retail order agents

- Pair case issue: [#58](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/58)
- Partners / GitHub usernames: Pin-Ray Liao (@bill255203), Yusuke Katsuki (@katsukii)
- Peer feedback / reviewer: maintainer review on this PR (2026-10-13); peer reviewer to be arranged
- Status: outline; development evidence collected, comparison not started
- Dated plan revision and available feedback: 2026-10-07 initial outline for M2; 2026-10-13 maintainer feedback; 2026-10-14 sections 4–5 updated with the repeated pilot and the task 4 trace review
- Individual task links: @katsukii [#62](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/62); @bill255203 [#64](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/64)

## 1. Business workflow

We study a retail customer-service agent that receives customer requests, checks order information and policies, and uses tools to perform permitted actions such as cancellations, returns, and exchanges. The agent must determine which actions are required and whether their results justify reporting completion.

We plan to explore two small proofs of concept: a synthetic inventory scenario and multi-request retail tasks from τ-bench.

Sources: the retail domain [policy](https://github.com/sierra-research/tau2-bench/blob/main/data/tau2/domains/retail/policy.md) and tools of [τ²-bench](https://github.com/sierra-research/tau2-bench). The setting is simulated: the store, customers and orders are synthetic, and customers are played by an LLM. Real store data and payments are outside the study.

## 2. Risk question

Can a final completeness check reduce missed requests or premature completion claims in retail order workflows?

These failures could leave customers believing an order change was completed when it was not, potentially causing additional support requests, delayed refunds, and lost trust.

Our proposed check asks the agent to compare each customer requirement with available tool results before reporting completion. This week, we will first inspect a small baseline to determine whether these failures occur. If feasible, we will try the check on a small sample and record task outcomes and additional tool calls. We do not yet claim that the check improves performance.

## 3. Prior work

Our starting references are [τ-bench](https://arxiv.org/abs/2406.12045) (Yao et al., 2024; code: [τ²-bench](https://github.com/sierra-research/tau2-bench)), [MAST](https://arxiv.org/abs/2503.13657) ([code](https://github.com/multi-agent-systems-failure-taxonomy/MAST)), and [Who&When](https://arxiv.org/abs/2505.00212) ([code](https://github.com/ag2ai/Agents_Failure_Attribution)). We will review τ-bench for reusable retail tasks and outcome evaluation, MAST for failure classification, and Who&When for failure attribution.

These provide starting points for evaluating outcomes and interpreting traces, but do not by themselves establish whether our proposed completeness check helps in the selected tasks. This week, we will confirm relevant methods and limitations and use the baseline traces to narrow the study.

## 4. Evidence and comparison

We use τ²-bench's retail domain (commit `5bfa7e37b366`): its tasks, tools, policy, simulated customer and state-based scoring. Each task's reference actions and goal database state serve as ground truth.

- **Development vs. evaluation.** Failure-seeking runs (repeating known failures, harder settings, cheaper models) are development work and are not reported as representative failure rates. Before any comparison, we will state the evaluation task subset, selection rule, models and trials, and keep them fixed across conditions.
- **Comparison.** The same agent without and with the completeness check: the agent re-checks each request against tool results before reporting completion; a separate verifier agent is a candidate design. Tasks, models, simulated customer, tools, policy, step limits and evaluator stay fixed.
- **Measures (per task, with denominators).** Task success under τ²-bench scoring; omitted requests; completion claims while a request is open; tool calls, tokens and cost. Infrastructure failures are recorded separately.
- **Labels.** Exact matching of expected tool calls only flags candidate failures, because equivalent calls can reach the correct state. Each omission is confirmed against the task's required final state and the trace, and we record whether the simulated customer actually conveyed the request.
- **Failure analysis without new runs.** τ²-bench publishes full runs of four models (`data/tau2/results/final`). After checking task-version compatibility, we will label their candidate failures before choosing evaluation tasks.

## 5. Feasibility and individual roles

- **POC 1 (exploratory, 2026-10-03).** A synthetic stock re-check in Colab with Gemini ran end to end, but its outcome mostly depended on what our setup showed the agent, so it says little about the agent's own decisions ([#62](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/62)). We focus on τ²-bench, whose retail tasks, data, tools and scoring are public (MIT license).
- **Development run 1 (2026-10-07).** [Notebook](../../experiments/tau2-retail/tau2_retail_baseline.ipynb): tasks with two or more expected state-changing tool calls; first five by ID (4, 11, 14, 16, 22); one trial each. All five were solved, assembled from four attempts whose other outcomes were infrastructure errors ([details](../../experiments/tau2-retail/README.md)).
- **Development run 2 (2026-10-07, repeated pilot).** [Notebook](../../experiments/tau2-retail/tau2_retail_pilot.ipynb): tasks whose reference solution changes two or more items (59 of 114); first ten by ID (0, 2, 4, 11, 13, 14, 16, 20, 21, 22); four trials each. The plan and decision rule were posted before running ([#62](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/62#issuecomment-6049640445)). 39/40 solved; all four trials solved in 9/10 tasks; 0 infrastructure errors.
- **Task 4 trace review.** The single failure came from the simulated customer, who asked about only one of two orders; in the passing trials the customer asked for all orders. It is a simulator issue, not an agent omission, so neither run shows a confirmed omission yet ([trace](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/62#issuecomment-6183015987)).
- **Settings and deviations.** Agent, simulated customer and judge: `gemini/gemini-3.8-flash`. τ²-bench's default judge (OpenAI gpt-4.1) was replaced, and a code fence is stripped before parsing the judge's JSON. Across the 40-run pilot, averages were about 56 seconds, 101K input tokens, 4.7K output tokens and $0.092 per run for the agent and simulated customer; judge usage is excluded. Run files are kept locally with SHA-256 checksums ([README](../../experiments/tau2-retail/README.md)).
- **Next.** The [τ-bench reading note](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/62#issuecomment-6064619007) is posted. Next, label candidate failures in the published runs; agree the evaluation subset, rules and a capped API plan (no course budget is provided; see [#74](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/74)). These runs show feasibility, not a failure rate or the effect of the check.
- **Roles.** @bill255203 drafted sections 1–3 ([#64](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/64)); @katsukii drafted sections 4–5 and ran the experiments ([#62](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/62)). Next responsibilities are being agreed.
