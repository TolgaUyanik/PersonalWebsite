# Projects — AwakenAnalytics Quant Platform

> Reference document for the project showcase on tolgauyanik's personal website.
> Audience: recruiters, hiring managers, fintech/analytics teams, and technically
> curious readers. Goal: communicate scope, engineering depth, and measurable
> impact of a personal algorithmic-trading research platform built end to end.
>
> **IP note:** This document is public-facing. It describes architecture, methods,
> and outcomes — it intentionally does **not** publish exact strategy rules,
> indicator thresholds, or model parameters. Those remain internal IP.

---

## The one-line pitch

> I built a full algorithmic-trading research platform — from automated strategy
> discovery, through rigorous backtesting and forward-testing, to a live
> Dockerized engine that scores markets daily and pushes buy/sell signals, all
> monitored through Grafana dashboards.

The platform targets **BIST-100 (Borsa İstanbul)** as its primary market and
**US large-caps** as a secondary market. It is the work of a solo developer
acting as quant researcher, data engineer, and ML engineer at once.

---

## Why split into five projects?

The original site grouped everything into three blocks (Strategy Miner,
Backtesting, StockMarketDocker). For personal branding, splitting into **five**
tells a stronger story: it shows the *complete machine-learning + quant
lifecycle*, and each stage maps to a recognizable, hireable skill.

| # | Project | Lifecycle stage | Skill it demonstrates |
|---|---------|-----------------|------------------------|
| 1 | **Strategy Miner** | Discover | ML feature engineering, search at scale |
| 2 | **Backtesting Framework** | Validate | Simulation rigor, statistical honesty |
| 3 | **Live Trading Engine** | Deploy | Production engineering, orchestration |
| 4 | **Analytics Dashboards** | Monitor | Data visualization, decision support |
| 5 | **Paper-Trading Quality Lab** | Verify | Forward-testing, scientific skepticism |

Together they read as one sentence: **discover → validate → deploy → monitor → verify.**
That arc is the brand. It shows you don't just train a model — you run the whole
loop a real quant desk runs, and you guard against fooling yourself at every step.

---

## Project 1 — Strategy Miner

**Tagline:** *An automated engine that searches hundreds of indicator
combinations to discover statistically robust trading strategies.*

### What it does
The Strategy Miner is a discovery engine. Instead of hand-coding a few trading
ideas, it systematically generates and tests a large search space of candidate
strategies built from technical indicators, then keeps only the ones that survive
strict statistical filters.

### How it works
- **Indicator engine:** computes 200+ technical indicators across a stock's full
  price history (momentum, trend, volatility, volume, and structure features).
- **Strategy factory:** auto-generates strategies across nine families —
  oscillator thresholds, crossovers, direction changes, band breakouts/reversions,
  moving-average crossovers, volume/momentum, Fibonacci/pivot, and level-based
  rules. Each strategy is expressed as a declarative signal rule.
- **Mining loop:** tests rule combinations against minimum-trade-count and
  minimum-profitability gates, then runs survivors through a multi-stage
  validation pipeline (multi-labeler agreement, expectancy checks, market-regime
  awareness, and walk-forward fold robustness).
- **Tiering:** strategies that pass all walk-forward folds are promoted to a
  "deploy" tier; weaker but promising ones are kept as "research" tier.

### Engineering highlights
- Single configurable mining script parameterized by forward horizon and target
  return — the same pipeline runs across daily and hourly bars and across
  multiple target levels.
- Universe filtering by liquidity (daily turnover) to avoid untradeable signals.
- Designed around the hard lesson that *in-sample brilliance means nothing* —
  every candidate must survive out-of-sample and walk-forward testing.

### Impact / proof points
- Reduced strategy discovery from manual trial-and-error to a repeatable,
  auditable pipeline.
- Surfaced a tiered library of validated strategies actually deployed to the live
  paper-trading engine (Project 3).

---

## Project 2 — Backtesting Framework

**Tagline:** *A simulation engine that pressure-tests strategies against years of
real market data with honest, cost-aware accounting.*

### What it does
Before any strategy is trusted, it runs through a five-phase backtesting pipeline
that simulates how it would have actually traded — including real-world frictions
that most naive backtests ignore.

### How it works
The pipeline runs in clear phases:
1. **Data manager** — downloads OHLCV data and caches it locally (Parquet) for
   fast, reproducible reruns.
2. **Indicator engine** — computes the full indicator set across the time series.
3. **Strategy factory** — instantiates the candidate strategies.
4. **Backtester** — simulates entries and exits bar by bar, applying a strict
   exit hierarchy: stop-loss → trailing-stop → max-hold → signal-reversal.
5. **Results analyzer** — writes ranked leaderboards and full per-trade logs.

### Engineering highlights
- **Cost-aware:** models real round-trip commission per market (a meaningfully
  higher rate for Borsa İstanbul than for US large-caps), so "profitable" means
  profitable *after costs*.
- **Multiple exit configurations** can be tested in one run to find the best
  risk-management envelope per strategy.
- **Ranking discipline:** strategies are scored on four metrics simultaneously —
  weighted Profit Factor, Sharpe ratio, Win Rate, and Consistency — and must
  clear all four to make the leaderboard. No cherry-picking a single flattering
  number.

### Impact / proof points
- Produces transparent artifacts every run: a ranked strategy leaderboard, a full
  trade-by-trade ledger, and a best-strategies-per-ticker table.
- Turned "I think this works" into "here is the after-cost, multi-metric,
  out-of-sample evidence."

---

## Project 3 — Live Trading Engine (StockMarketDocker)

**Tagline:** *A Dockerized, cron-driven engine that scores markets daily and
dispatches live paper-trading signals — production-grade, hands-off.*

### What it does
This is the deployment layer: a containerized service that wakes on a schedule,
decides which market is most attractive to trade today, runs the deployed
strategies, manages open positions, and pushes buy/sell alerts.

### How it works
- **Daily orchestrator (main run):** scores each candidate market on a 0–100
  scale. If the best market scores below a "sit-out" threshold, the engine trades
  nothing that day and only manages exits — a deliberate capital-protection rule.
  Otherwise it dispatches the winning market to its paper-trading routine.
- **Intraday runs:** hourly jobs evaluate short-horizon BIST strategies during the
  trading session.
- **Position management:** every run checks open positions against the exit
  hierarchy (stop-loss → trailing-stop → max-hold → signal-reversal).
- **Alerting:** trade signals are pushed to Slack in real time.
- **Self-retraining:** scheduled jobs retrain the market-regime model quarterly
  and the entry model monthly, so the system adapts without manual intervention.

### Engineering highlights
- **Fully containerized** with Docker Compose — reproducible deployment, one
  command to stand up the whole stack.
- **Cron-scheduled** around real market hours (in UTC, aligned to Borsa İstanbul
  and US sessions).
- **Stateful** via SQLite databases tracking open positions, closed trades, market
  scores, and routing decisions across multiple markets.
- **ML in the loop:** a regime-detection model (Hidden Markov Model) classifies
  the market environment, and a random-forest entry gate filters signals.

### Impact / proof points
- Runs unattended day after day, turning the research pipeline into a living
  system rather than a notebook.
- Demonstrates the leap most data projects never make: from analysis to
  *operational, scheduled, monitored production*.

---

## Project 4 — Analytics Dashboards (Grafana)

**Tagline:** *Daily and hourly market dashboards with clear buy/sell
recommendations — the human-facing window into the engine.*

### What it does
A suite of Grafana dashboards visualizes the platform's analysis: technical
indicators, market scores, regime classification, and the day's buy/sell
recommendations — for both BIST and US markets, on daily and intraday cadences.

### How it works
- Scheduled analysis jobs refresh dashboard datasets at set times each day
  (a fast intraday refresh, an end-of-day summary, and a global-market view).
- Grafana reads the SQLite databases directly via a SQLite datasource plugin —
  no heavy data warehouse needed.
- Dashboards present indicator signals, ranked opportunities, and current market
  regime in a form a human can scan in seconds.

### Engineering highlights
- Lightweight architecture: SQLite + Grafana, no over-engineering.
- Separate daily and hourly views, and separate BIST and US views, so each market
  and timeframe gets its own focused board.
- Designed as *decision support* — the dashboards translate model output into
  actionable, glanceable recommendations.

### Impact / proof points
- Makes an otherwise opaque ML pipeline legible and trustworthy at a glance.
- A live Grafana snapshot is already embedded on the personal site
  (`SMGrafana.html`).

---

## Project 5 — Paper-Trading Quality Lab

**Tagline:** *Forward-testing dashboards that grade live strategy quality in real
time — proof a strategy works in the present, not just the past.*

### What it does
Backtests can lie; markets change. The Quality Lab forward-tests the deployed
strategies on live, unseen data and tracks how they actually perform — the
scientific safeguard that separates a hobbyist from a quant.

### How it works
- Each deployed strategy runs in paper-trading mode: it takes simulated positions
  on live signals, with the same exit rules and realistic commission accounting as
  the backtester.
- Results accumulate in dedicated databases (separate ledgers for daily BIST,
  hourly BIST, and US strategies), then surface in quality dashboards.
- Performance is judged on the same honest metrics as backtests — profit factor,
  win rate, monthly consistency — so a strategy's live grade is directly
  comparable to its historical grade.

### Engineering highlights
- **Two parallel pipelines:** a v1 engine and a newer canonical v2 pipeline run
  side by side on the same schedule with separate databases, so new strategy
  generations can be validated without disturbing the proven ones.
- **Brutal honesty built in:** strategies that look great in-sample but lose money
  out-of-sample are *retired* — and the lab is the mechanism that catches them.
- Tracks per-strategy, per-month profitability to distinguish genuine edge from
  lucky streaks.

### Impact / proof points
- Caught and retired strategies that had inflated in-sample results but were real
  net losers live — the single most important discipline in quant work.
- Closes the loop: discoveries from Project 1 are continuously re-validated
  against reality, so the platform self-corrects over time.

---

## How the five fit together

```
  ┌──────────────┐   ┌──────────────┐   ┌──────────────────┐
  │ 1. Strategy  │──▶│ 2. Back-     │──▶│ 3. Live Trading  │
  │    Miner     │   │   testing    │   │    Engine        │
  │  (discover)  │   │  (validate)  │   │   (deploy)       │
  └──────────────┘   └──────────────┘   └────────┬─────────┘
         ▲                                        │
         │                                        ▼
         │            ┌──────────────┐   ┌──────────────────┐
         └────────────│ 5. Quality   │◀──│ 4. Analytics     │
            feedback  │    Lab       │   │    Dashboards    │
                      │  (verify)    │   │   (monitor)      │
                      └──────────────┘   └──────────────────┘
```

Discovery feeds validation, validation feeds deployment, deployment is monitored,
monitoring is verified — and verification feeds back into discovery. A complete,
self-correcting quant research loop, built solo.

---

## Tech stack (for the skills/keywords section)

- **Languages:** Python
- **ML / data:** scikit-learn (random forests), Hidden Markov Models, pandas,
  NumPy, feature engineering, walk-forward validation
- **Quant methods:** technical indicators (200+), profit factor, Sharpe ratio,
  backtesting, forward-testing, regime detection, market scoring
- **Infra / ops:** Docker, Docker Compose, cron scheduling, SQLite, Grafana,
  Parquet caching, Slack alerting
- **Data sources:** Yahoo Finance (yfinance)
- **Markets:** Borsa İstanbul (BIST-100), US large-caps

---

## Suggested website wording (short cards)

Drop-in copy for the `#projects` / `#StockMarket` section of `index.html`. Each is
short enough for a Bootstrap project card.

**Strategy Miner**
> An automated engine that searches hundreds of indicator combinations to
> discover statistically robust trading strategies — every candidate survives
> walk-forward and out-of-sample testing before it ships.

**Backtesting Framework**
> A five-phase simulation engine that pressure-tests strategies against years of
> market data with honest, commission-aware accounting and four-metric ranking
> (profit factor, Sharpe, win rate, consistency).

**Live Trading Engine**
> A Dockerized, cron-driven service that scores markets daily, sits out when
> conditions are poor, dispatches live paper-trading signals, manages exits, and
> retrains its own models on schedule.

**Analytics Dashboards**
> Grafana dashboards turning the engine's output into glanceable daily and hourly
> buy/sell recommendations across BIST and US markets.

**Paper-Trading Quality Lab**
> Forward-testing dashboards that grade live strategy quality in real time — the
> scientific safeguard that retires strategies which only *looked* good in the
> past.

---

## Notes for future edits

- Keep exact strategy rules, thresholds, and model parameters **out** of this file
  and the website — public repo.
- Update impact numbers (trade counts, profit factors, months-profitable) from the
  latest leaderboard/quality-lab runs when refreshing the site, but keep them
  qualitative enough not to leak rule specifics.
- Candidate hero images already in `assets/img/`: `Finance.jpg`, `hourglass.webp`,
  `StockMarket.jpg`, `Python.jpg`.
- If adding these as real site sections, follow the existing alternating
  image/text row pattern in `index.html` (`.row .col-lg-6` blocks).
```
