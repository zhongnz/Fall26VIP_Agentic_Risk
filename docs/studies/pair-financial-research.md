# Pair case — Financial Research Citation Verification

- Pair case issue: [#65](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/65)
- Partners / GitHub usernames: [@geenana](https://github.com/geenana), [@zq2082](https://github.com/zq2082) 
- Peer feedback / reviewer (when arranged; no mentor assignment needed to start): To be arranged 
- Status: outline 
- Dated plan revision and available feedback: 2026-10-07 — Initial short case outline completed; no peer feedback yet. 
- Individual task links: [@geenana](https://github.com/geenana) - [#66](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/66); [@zq2082](https://github.com/zq2082) - [#67](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/67) 

Start with sections 1–5, about half a page. Expand this same document into the report.
Examples and pending work must not be represented as findings. Do not fill fields
with invented partners, approvals, sources, or results.

## 1. Business workflow

An AI agent reviews public financial documents, such as SEC filings, earnings releases, and investor presentations, and answers a research question with citations.

The intended workflow is:
- User asks a financial research question.
- Agent reads the provided documents.
- Agent produces an answer with citations.
- Analyst uses the answer and citations for review.

## 2. Risk question

**Risk**: The agent may attach citations that do not actually support the claims made.
This can make an incorrect answer look credible and increase the analyst’s review burden.

**Question**:
Does an explicit post-generation citation verification step reduce unsupported claims compared with citation generation alone, while preserving useful task completion?

**Comparison**:
- Baseline: agent answers and generates citations.
- Treatment: after drafting, the agent checks each material claim against the cited source and removes, revises, or qualifies unsupported claims.

## 3. Prior work

- [Effective Large Language Model Adaptation for Improved Grounding and Citation Generation](https://aclanthology.org/2024.naacl-long.346.pdf) 
- [CiteAudit: You Cited It, But Did You Read It? A Benchmark for Verifying Scientific References in the LLM Era](https://arxiv.org/abs/2602.23452) 
- [VeriCite: Towards Reliable Citations in Retrieval-Augmented Generation via Rigorous Verification](https://dl.acm.org/doi/abs/10.1145/3767695.3769505) 
- [Citation Failure: Definition, Analysis and Efficient Mitigation](https://arxiv.org/abs/2510.20303) 

## 4. Evidence and comparison

Use a small initial development set:
- 3–5 public financial documents;
- 6–10 research questions;
- expected answers;
- manually checked supporting passages.

For each question, run both the baseline and treatment and save the prompt, response, citations, source documents, and claim-level labels.

Each material claim will be labeled:
- **Supported**
- **Unsupported**
- **Ambiguous**

Main comparison:

- **Unsupported Claim Rate (UCR)** = Unsupported Claims / Total Material Claims

## 5. Feasibility and individual roles

[@zq2082](https://github.com/zq2082) — Evidence setup
- Select the initial documents.
- Create 6–10 research questions.
- Record expected answers and supporting passages.
- Draft the claim-labeling rules.

Deliverable: small reference dataset. 

[@geenana](https://github.com/geenana) — Experiment setup
- Create the baseline prompt.
- Create the verification prompt.
- Run both conditions.
- Save outputs and citations.
- Prepare the claim-level comparison table.

Deliverable: reproducible baseline vs. verification runs. 

## 6. Working method

As the study develops, record the applicable details below. This is a working
method, not an instructor approval form. State evaluation rules before applying
them, seek peer feedback and record changes after inspecting evidence.

- Evidence route; exact platform/data/model versions as applicable.
- Unit of analysis, data selection, development versus evaluation split; prior inspection and its effect on claims.
- Comparison and what remains fixed; labels and how they are checked.
- Measures with numerators/denominators; risk, utility and relevant cost.
- Sample/repetition plan, treatment of dependent observations, uncertainty/claim limits.
- Failure, exclusion, retry, stopping and analysis rules.
- Resources, validation evidence, available feedback, and dated changes with reasons.

For existing-trace work, specify labeling rules and an agreement check. Use only
applicable fields from the [experiment record](../experiment-record.md).

## 7. Results and interpretation

Add actual evidence links, counts, comparisons and appropriate uncertainty. Include
failures, missing data, null findings and deviations. State what the evidence supports,
what it does not establish, and whether the proposed improvement was actually tested.

## 8. Contributions, reproduction and next steps

Identify each student's work with task/PR links, including review and tool assistance.
Give artifact locations, exact analysis/run instructions and access requirements.
Link a peer's reproduction/source check, known limitations and next useful question.
Link midterm/final slides and both individual reports. Cite sources where used.
