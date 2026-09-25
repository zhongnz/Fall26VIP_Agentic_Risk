# Choose and develop your pair case

Each pair chooses **one business workflow, one risk question, and one possible
improvement**. The cohort shares methods and feedback; there is no competition to
select a single cohort-wide study. Pair membership and working plans are recorded
in [#3](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/3) and linked Pair case issues.
No platform, case, or protocol is automatically adopted. Partners choose a small
scope and proceed with peer feedback; instructor sign-off is not a prerequisite.
The instructor can redirect or adapt the work as needed. See
[review responsibilities](../issue-workflow.md#who-reviews-what).

Under **Agentic AI for Risk Management**, the [research focus](../research-plan.md#shared-theme)
is risk assessment and improvement of agentic business workflows. Start with a
real business use case, explain the agent's role and intended benefit, and choose
one risk question. Its question determines the evidence and comparison; propagation
is one possible direction.

## Short proposal outline

Start with about half a page using the first five sections of the
[case template](_case-template.md). Copy it to `docs/studies/pair-CASE-SLUG.md` and
link it from the Pair case issue. Expand that same document as the study develops;
it becomes the final report, avoiding a separate proposal/report to maintain.

1. **Business workflow:** who needs what done, which actions the agent can take,
   and the policy/source supporting this real business need.
2. **Risk question:** one risk in the agentic workflow, its business consequence,
   and one answerable question about how to assess or address it.
3. **Prior work:** a few relevant sources; what remains uncertain or why replication helps.
4. **Evidence and comparison:** what will be observed, compared, or labeled; how
   decision quality, failures and useful outcomes will be judged; one possible improvement to assess.
5. **Feasibility and roles:** accessible environment/traces, smallest check, needed
   support, and each partner's next Individual task.

Candidate A is an **optional advanced example** of a mature protocol, not a required
continuation of the starter or the expected detail of a first student outline.

## Examples of bounded questions

These **seven optional starting ideas** are business workflows to narrow, not
prepared studies or supplied datasets. Choose one, adapt it, or propose another
workflow within the shared scope. Multiple pairs may choose the same workflow
for complementary questions or a deliberate replication; topics are not reserved
by the first pair to choose them. Link related Pair cases and credit shared work.

| Possible workflow | Example bounded question | Small evidence route to check |
| --- | --- | --- |
| Financial research | Does checking cited source text reduce unsupported claims in an agent's research summary? | A fixed set of public documents and questions, with checked reference answers; compare runs with and without the check, including useful answers completed. |
| Compliance | Does a source-version check reduce decisions based on outdated policy text? | A documented policy, clearly labeled outdated excerpts and matched tasks; check incorrect decisions and correct completion with and without the safeguard. |
| Customer service / refunds | Does checking source evidence before an agent's refund action reduce incorrect refunds? | The same policy-based tasks with and without the check; incorrect actions, correct completion and relevant cost. |
| Procurement / order processing | When order details conflict, does an agent escalate appropriately or act on unsupported information? | If genuine traces are accessible, compare conflicting versus consistent orders using a declared sample, documented policy and checked labels. Measure incorrect actions, appropriate escalation and useful completion; observed differences do not establish causes. |
| Software / operations | Does validating tool output reduce incorrect file changes? | Agent runs in a small sandbox with defined permitted edits; compare a validator with no validator on matched tasks using clean and corrupted tool outputs. Check incorrect edits and valid tasks completed. |
| Supply chain / inventory | Does refreshing a stale inventory record reduce commitments that cannot be fulfilled? | A small simulated ordering workflow with known stock and matched agent tasks; compare refresh versus no refresh, including correct orders completed. |
| Credit / risk review | When application records conflict, does the agent flag them before making a recommendation? | Synthetic records, explicit review rules and checked labels; compare conflicting and consistent inputs. Assess rule-following and useful completion, not real-world creditworthiness. |

For every idea, establish the business motivation from sources and verify that the
needed environment or traces are accessible. Simulated inputs need genuine model
runs for claims about agent behavior. See the [resource starting points](../literature.md#choose-a-starting-route).
An improvement inferred from trace analysis remains a recommendation until tested.

Start with one workflow, one main comparison and a small development example.
Establish that the evidence is accessible before expanding the study. Choose enough
distinct cases to support the intended claim; a handful of examples may justify
an exploratory finding, not a general effectiveness claim. Reuse existing tools
and choose another accessible route if setup dominates the research. Neither a
multi-agent system nor implementing a new framework adds academic value by itself.

Keep measurement focused: choose one primary risk outcome and a relevant measure
of useful work. Add cost, latency, propagation depth or persistence only when the
question needs them. Define units and denominators; allow "not applicable" when
a measure does not fit. For a propagation question, trace the error's origin,
later influence, consequence and any containment; a wrong final answer alone does
not establish the path. [Shared-study guidance](../cohort-guide.md#sharing-an-experiment)
explains how pairs can collaborate without merging incompatible results.

## Selection and protocol

- **M2 target (Oct 9):** agree the short outline, partners, scope, and evidence
  route. Ground the case in public or approved business sources; do not promise
  company access, a new framework, or publication.
- **M3 target (Oct 16):** present the case and initial feasibility evidence. Expand
  the plan as needed to state comparison, data selection, units, labels,
  measures/denominators, sample/repeat plan, failures/exclusions, analysis, resources,
  and claim limits. Link a dated revision and feedback in the Pair case.
- **As evidence work develops:** validate the smallest analysis/run, state evaluation
  cases and rules before applying them, and distinguish development evidence. Seek
  help with sample size when needed. A few smoke-test examples establish feasibility,
  not a reliable effect estimate.
- **Afterward:** record amendments and whether results had been inspected. If access
  fails, narrow the question and seek help if needed; do not invent missing evidence.

These are adjustable targets. Routine changes need a short note in the existing
case, not an approval process. A claim described as confirmatory still requires
its hypotheses and evaluation rules to be set before examining test outcomes.

If evidence has already been inspected, document which records were used for
development and reserve new records where feasible. Otherwise frame the affected
analysis as exploratory or replication work; do not claim a fresh held-out test.
A trace analyst may read evaluation records to apply fixed labels, but changing the
labeling guide or hypothesis after seeing them requires a recorded amendment.

Each pair progresses independently; an unassigned mentor or open cohort issue does
not block work. Arrange peer checks before presenting findings as checked. Pairs
may share an environment or compare complementary questions, while preserving
their own measures and claim boundaries.

## Two manageable evidence routes

**Small comparison or replication:** reuse a supported environment, reproduce its
baseline, and assess one change or prior claim. Use genuine model runs when making
claims about model behavior. Measure decision quality, errors, useful outcomes
and relevant cost as the question requires. Test the evaluator itself on known
examples. A rules-based baseline can be a meaningful comparison; document the
information and resources available to each method.

**Structured trace analysis:** use genuine accessible execution records, a declared
sampling rule and comparison, and a clear labeling guide. Have another person label
an overlapping subset; report agreement and resolve discrepancies transparently.
This can assess decision quality, failure patterns or evidence gaps in the sampled
records. It cannot establish an untested improvement's causal effectiveness.
Frame the improvement as a recommendation unless there is suitable comparative evidence.

Both routes require empirical evidence. Scripted starter results and hypothetical
risk maps alone are teaching/design outputs. If the instructor adapts the assessed
scope to a literature/design study, record that direction and use narrower claims;
do not present it as an empirical result. A course discussion or announcement can
establish that change without a separate approval form.

## Shared standards, flexible implementation

Both partners should understand the workflow, evidence and analysis. Code is useful
when it produces or checks evidence; no line-count target or large system is required.
Scenario design, labels, validation, and a reproducible analysis can be substantial
technical contributions. Rotate roles with guidance.

Agent Assurance supplies hypotheses and evidence practices alongside other literature.
No named framework or full control matrix is required. See [research standards](../research-plan.md),
[resources](../literature.md), and the [schedule](../semester-plan.md).
