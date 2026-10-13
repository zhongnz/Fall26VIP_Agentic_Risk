# Pair case — Risks in a multi-agent trading workflow (TradingAgents)

- Pair case issue: [#71](https://github.com/zhongnz/Fall26VIP_Agentic_Risk/issues/71)
- Partners / GitHub usernames: @lisasiliu, @sm11t, @arghyas2 (Arghya Srivastav); team of three
- Peer feedback / reviewer (when arranged; no mentor assignment needed to start): to be arranged
- Status: outline
- Dated plan revision and available feedback: 2026-10-07 initial outline from team idea discussion
- Individual task links: TBD

## 1. Business workflow

An investment-research desk wants an agent system to turn market data, news and
sentiment into a trade decision (buy / hold / sell) for a given ticker and date. The
workflow under study is the open-source TradingAgents multi-agent framework, in which
LLM-backed roles (analysts, researchers who debate, a trader, risk review) exchange
reports and reach a consensus decision.

| Item | Detail |
| --- | --- |
| Roles | Analyst, researcher, trader (and related roles in the framework) |
| Inputs | Historical or live price data, news, social/sentiment sources |
| Allowed action | Produce a trade decision; in live tests, paper-trade only |
| Simulated | Backtests and paper trading; no real money |
| Out of scope | Real-money trading, claims of profitability |

## 2. Risk question

Core risk: the framework's reported performance may not be a reliable guide to how the
workflow behaves, because of how it is evaluated and configured. Business consequence:
a desk could deploy a decision workflow whose measured quality is overstated or whose
consensus is fragile.

The case examines four candidate questions. The pair/team should narrow to one
primary question and treat the rest as follow-ups (see section 5).

1. **One-off events.** How does the framework behave in backtests over single volatile
   events (e.g. crypto in 2024; oil in Feb 2026, Strait of Hormuz)? The original paper
   tested one 3-month period; how many periods are needed for a credible study?
2. **Single-model monoculture.** Does using one backend model for every role weaken the
   value of inter-agent debate and consensus, compared with assigning different model
   families to different roles?
3. **Backtest contamination.** Jan–Mar 2024 data may not be out of sample for the
   commercial models used. Does behavior differ on current live data, using Alpaca
   paper trading (post-training-cutoff, no real money)?
4. **Source weighting in sentiment.** The framework does not weight sentiment by source
   (e.g. follower counts). How many opposing sources are needed to flip the sentiment
   decision, and does this differ for small tickers versus large ones (e.g. NVDA)?

Possible improvement to assess: for each question, a concrete mitigation (more
evaluation windows, heterogeneous model assignment, live out-of-sample checks, source
weighting). Any improvement stays a recommendation until tested.

## 3. Prior work

- Xiao et al., [TradingAgents: Multi-Agents LLM Financial Trading Framework](https://arxiv.org/abs/2412.20138) ([PDF](https://arxiv.org/pdf/2412.20138)), and its [open-source repository](https://github.com/TauricResearch/TradingAgents). Establishes the role-based multi-agent design and reports results on one Jan–Mar 2024 window; whether those results hold in other periods, with other models, or out of sample is what this case examines.
- Alpaca documentation for the live-data route: [paper trading](https://docs.alpaca.markets/docs/paper-trading) and the [Alpaca MCP server](https://docs.alpaca.markets/docs/alpaca-mcp-server) ([repository](https://github.com/alpacahq/alpaca-mcp-server)). A free Alpaca account is needed for paper-trading keys.

Open item: add further primary sources (e.g. on LLM training-data contamination and multi-agent debate) for questions 2–4 before relying on them.

## 4. Evidence and comparison

To be fixed per chosen question before results are inspected. Sketches:

- Q1: backtest the unchanged framework over several event windows; compare decision
  outcomes across windows; report variation, not just one aggregate.
- Q2: same tickers/dates with (a) one model in all roles vs (b) different model
  families per role; compare decisions, agreement and downside outcomes.
- Q3: compare behavior on the original Jan–Mar 2024 window vs current live/paper data.
- Q4: hold a ticker and date fixed; inject increasing numbers of opposing-sentiment
  sources and record the count at which the decision flips; repeat across small and
  large tickers.

Backtest returns are not proof of real-world profitability. Repeated LLM runs vary, so
plan repetitions and report uncertainty.

## 5. Feasibility and individual roles

- Accessible now: TradingAgents code (open source); Alpaca paper trading (free). Model
  API budget is the main open cost; to be confirmed.
- Not yet checked: data access for the 2024 crypto and Feb 2026 oil windows.
- Proposed first step: run the framework once end-to-end on one ticker/date as the
  smallest feasibility probe.
- Roles: not yet assigned. Each student opens their own Individual task under this
  case and chooses a question (one question per person is a natural split). Roles to
  be agreed by the team.

## 6. Working method

To be filled once the primary question is chosen. Record evaluation rules before
running experiments.

## 7. Results and interpretation

None yet.

## 8. Contributions, reproduction and next steps

None yet.
