# Literature Starting Point

This is a seed list, not a completed literature review. Paper links point to primary arXiv records; platform links point to official projects. Descriptions are deliberately limited to what the papers say they contribute; students should read and assess the methods before relying on any result.

## Start here: basic concepts

- **Agentic workflow:** a model uses information and tools to take steps toward a task.
- **Tool:** an operation it can request, such as looking up an order or changing a record.
- **Authority:** what actions it is permitted to take; permission does not ensure correctness.
- **Risk:** a possible adverse outcome for the business or user, including poor decisions, losses or failures.
- **Risk assessment:** examining where an agentic workflow can fail, the potential consequences, and what evidence supports that assessment.
- **Control:** a check or restriction intended to reduce a failure or consequence.
- **Trace:** a record of observable inputs, tool calls/results, responses and actions.
- **Baseline:** the comparison used to judge whether a proposed change helps.
- **Utility:** useful work completed; a safeguard that blocks everything may be ineffective overall.

## A small reading path

Read with a question in mind; nobody is assigned this whole list.
Choose sources for your own question within the [broad research scope](research-plan.md#shared-theme).
The propagation and attribution references below are useful options, not a required focus.
This seed list emphasizes agent evaluation and safeguards. Use business-process
and policy sources to establish the workflow's purpose, intended benefit and
consequences of failure; use relevant research to design the investigation.
Benchmark results alone do not establish effectiveness in a real business.

1. **Common guided methods reading:** [AI Agents That Matter](https://arxiv.org/abs/2407.01502)
   (Kapoor et al., 2024). Focus on cost, held-out evaluation and reproducibility.
   Discuss selected sections with a partner or in the cohort; students need not master every method first.
2. **One methods or application paper relevant to your case:** choose research on
   the workflow's risks, evaluation method or a relevant environment. Examples include
   [tau-bench](https://arxiv.org/abs/2406.12045) (Yao et al., 2024) for business
   interactions with policies/tools and final-state evaluation, and
   [AgentDojo](https://arxiv.org/abs/2406.13352) for prompt-injection attacks/defenses
   and legitimate task utility. Neither environment is required.
3. **A few focused sources:** find the business policy/process and prior research
   directly informing your question. Split reading between partners and explain it
   to each other; there is no fixed paper-count quota.

For each assigned reading, write a short note in your task or case document:
**question; evidence/method; one limitation; implication for our case**. Link the
source and relevant section. Expand only when the case needs deeper review.

## Choose a starting route

Pick the route that fits your question and current access. You do not need to
install every platform or build a new agent framework.

| Your immediate need | Where to start | Smallest useful check |
| --- | --- | --- |
| Understand a trace before choosing a method | [Optional starter walkthrough](starter-walkthrough.md) | Explain one worked trace and its limits; no API needed. This is practice, not empirical agent evidence. |
| Compare agent decisions or one safeguard | A relevant existing environment from the [platform candidates](#platform-candidates-test-only-what-your-case-needs) | Inspect one task, its policy and outcome rules; with suitable access, capture a baseline run and verify how its result is scored. |
| Analyze existing failures or evidence gaps | Accessible genuine traces linked by a primary source or shared in [#6](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/6) | Verify the records can actually be obtained, their reuse conditions, and whether one trace contains enough information to apply your proposed labels. Availability is not assumed. |

A first successful check establishes feasibility, not a reliable effect estimate. Record
it in your existing task or case: **source/version; command or sample; outcome
check; access/cost; limitations**. Link reusable instructions in #6 so another pair
can benefit. Mark a resource as tested only for the setup you actually checked;
an official documentation link alone is an untested candidate. If blocked, record
the blocker and narrow the next step with your partner.

## Platform candidates: test only what your case needs

| Resource | Possible use | Preparation needed |
| --- | --- | --- |
| [tau-bench family](https://github.com/sierra-research/tau2-bench) | Candidate for a small text-based retail/airline business example. | Pin a version and task subset; test setup, model/user-simulator access, costs, outcomes and saved traces. Current repository has evolved beyond the original paper. |
| [AgentDojo](https://agentdojo.spylab.ai/) | Alternative for risks caused by malicious content in tool outputs. | Test a narrow suite, attack/defense and utility evaluation; API/setup may change. |
| [Inspect AI](https://inspect.aisi.org.uk/) | Optional evaluation machinery for a custom case. | Requires defining tasks/agents/scorers; not itself a ready business-case curriculum. |

**None is adopted or installed by this plan.** A pair can try an accessible resource
and share useful instructions or a help request in [#6](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/6). There is no requirement for
the instructor or each pair to prepare a platform package. Start with a benchmark's
native runner if useful; keep setup bounded and choose another route if it dominates
the work. Record actual access and versions; obtain authorization before paid use.
The local scripted starter needs no API. Genuine saved agent traces must be sourced
and checked for a case that relies on them; no central dataset is promised.

Use [the case guide](studies/README.md) to choose a bounded question. Reusing a
benchmark can support rigorous replication or extension, but it does not establish
novelty or effectiveness in a real company. Agent Assurance is an optional source of
hypotheses; the [source map](agent-assurance-bridge.md) explains scope and limitations.

## Advanced references — consult only as needed

The remaining list supports specific cases. It is not the first-week reading load.

### Additional resources to evaluate selectively

These references serve different purposes. Reading a paper, reusing its data,
running its code, and adopting a framework are separate decisions. No row is a
mandatory integration or an established result about our own study.

| Resource | Why inspect it | Scope to keep clear |
| --- | --- | --- |
| [SABER: Small Actions, Big Errors](https://arxiv.org/abs/2512.07850) | Studies state-changing actions and combines targeted verification, reflection, and context management. Relevant prior work for any claim about safeguards at action boundaries. | Its observations and combined intervention do not establish our proposed gate's effect. A consequential error can also be an incorrect no-change decision. |
| [CAGE](https://github.com/google/cybernetic-agent-governance-engine) | An architectural reference for execution mediation and other runtime controls. A bounded mechanism could inform a question or comparator. | A control-boundary invariant does not demonstrate practical detection or utility. Full integration, formal models, or richer routing need a selected scientific purpose. |

Use exact paper/code/data revisions in a reproduction. Check actual access, setup,
licensing, and resource requirements before selecting a dependency. A reused
benchmark can support independent research when the question and interpretation
are clear; a fresh framework implementation is not itself an academic contribution.

### Multi-agent adversarial risk and propagation

#### [TAMAS: Benchmarking Adversarial Risks in Multi-Agent LLM Systems](https://arxiv.org/abs/2511.05269) — arXiv:2511.05269

TAMAS presents a benchmark for adversarial robustness in multi-agent LLM systems. Its abstract describes five scenarios, 300 adversarial instances across six attack types and 211 tools, 100 harmless tasks, ten backbone models, and three interaction configurations. It also proposes an Effective Robustness Score intended to combine safety and task effectiveness.

**Why it matters here:** it provides relevant benchmark structure, adversarial baselines, and an explicit safety–utility tradeoff. It also means that “multi-agent systems can propagate adversarial failures” should not be presented as this project’s novelty.

#### [ACIArena: Toward Unified Evaluation for Agent Cascading Injection](https://arxiv.org/abs/2604.07775) — arXiv:2604.07775

ACIArena studies cascading injection across external inputs, agent profiles, and inter-agent messages, with several attack goals and multi-agent implementations. The authors report that topology alone does not explain robustness, and that role design, interaction controls, and transfer across settings matter.

**Why it matters here:** it is directly related to cascading failure and control evaluation. The cohort should compare its threat model and outcome definitions with ACIArena rather than claim cascading injection is unstudied.

### Failure attribution and observability

#### [Seeing the Whole Elephant: A Benchmark for Failure Attribution in LLM-based Multi-Agent Systems](https://arxiv.org/abs/2604.22708) — arXiv:2604.22708

This paper introduces TraceElephant, a benchmark for failure attribution using full execution traces and reproducible environments. The authors compare full-trace and partial-observation settings and report substantially better attribution when inputs and context are retained.

**Why it matters here:** it motivates keeping complete, structured execution evidence instead of final outputs alone. It studies attribution; our initial pilot uses known injected faults and should not imply that logging by itself solves automated attribution.

#### [Which Agent Causes Task Failures and When? On Automated Failure Attribution of LLM Multi-Agent Systems](https://arxiv.org/abs/2505.00212) — arXiv:2505.00212

This work formulates automated failure attribution and introduces the Who&When dataset, built from failure logs with labels for responsible agents and decisive error steps. Its reported benchmark results show that locating the responsible step remains difficult even when methods can sometimes identify the agent.

**Why it matters here:** it offers task definitions, annotations, baselines, and cautions for any later attribution study. The first pilot knows where it injects a fault; that is ground truth for propagation measurement, not evidence that the system can infer responsibility in an unknown incident.

## How to use this list

For a deeper case-specific review, record the applicable details:

- the research question, threat or failure model, system boundary, and unit of analysis;
- datasets, models, agent frameworks, controls, baselines, and outcome denominators;
- whether code, data, prompts, and traces are available and reproducible;
- what the evidence directly supports and what the discussion only proposes;
- similarities to and differences from the candidate question and proposed comparison;
- one concrete implication for this project’s experiment design.

If the case requires a broader search, combine its business workflow with the
relevant research topic: reliability, decision quality, human oversight, tool
permissions, security/privacy, failure attribution, propagation or safety–utility
evaluation. Record search sources, query strings,
inclusion criteria, and the version of each reviewed paper.

Related work does not establish this project's novelty. A documented review helps
show what is answered, which methods can be reused, and where a defensible gap may
remain. A deliberate replication is also a valid choice when its purpose is clear.
Describe the selected study at the level its actual evidence supports.
