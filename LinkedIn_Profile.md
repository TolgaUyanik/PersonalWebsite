# Tolga Uyanik — LinkedIn Profile

*Final content reference. Each section below maps to a corresponding LinkedIn UI field. Copy/paste into the matching slot.*
*Last updated: 2026-05-08*

---

## Header

**Name:** Tolga Uyanik

**Headline** *(220 char max · using ~100)*:

> Quantitative Researcher · ML Trading Strategies · Alternative Data Products | Analyst @ De Canaria

**Location:** Antalya, Turkey

**Profile URL:** linkedin.com/in/tolgauyanik

**Personal Website:** tolgauyanik.github.io/PersonalWebsite/

**Email:** uyaniktolga123@gmail.com

**GitHub:** github.com/TolgaUyanik

---

## About

*~190 words / ~1,100 chars · LinkedIn max 2,600.*

> **Greetings!** I am Tolga.
>
> I work as an analyst at Canaria, a Job Market Intelligence platform. On any given day, I might be running competitor analysis on a dataset, shaping a new feature for one of our marketplace datasets, building marketing automation on behavioral signals, screening candidates, or fixing a scraper that just broke. The thread across all of it is product judgment: small decisions about messy data that compound into a better product.
>
> Outside work, I run my own three-stage quantitative research pipeline. A real-time monitor tracks BIST equities and computes 70+ indicators. A backtesting engine simulates trades under realistic transaction costs (including the actual Ziraat Yatırım commission, because details like that matter). A strategy miner uses XGBoost and Random Forest to surface patterns I'd never spot by hand. Top strategies hit 72–74% win rates and Profit Factors up to 9.5 in backtesting; live paper trading is the honest stage where I find out which ones survive.
>
> You can find raw data anywhere. But if you want it clean, enriched, and structured for a specific use case, you need someone who lives in that problem. With financial data, that's me. I build the product for myself, which is why I know exactly what good looks like and how to use it.

> **Formatting note:** LinkedIn's About field doesn't render markdown bold. To display "Greetings!" in bold, paste it through a Unicode-bold converter (e.g., yaytext.com → "Sans Bold") *before* pasting into the LinkedIn field.

---

## Experience

### 1. Analyst
**De Canaria · Jul 2023 – Present**

> Action-driven analyst role at a Job Market Intelligence platform. The analysis is just the start; once I find what's missing or broken, I build what comes next. Five hats: data product operations, competitor analysis, marketing automation, recruiting, and web scraping.
>
- • **Data product operations:** Generate and maintain proprietary alt-data product listings across three marketplaces (Datarade, EagleAlpha, Neudata); coordinate with enterprise buyers; keep dataset documentation, sampling, and pricing aligned with the market.
- • **Competitor analysis & feature development:** Run feature-gap analysis against competitor data samples; surface findings that drive new dataset features and quality improvements.
- • **Marketing automation:** Built and operate an end-to-end email marketing automation pipeline driven by segmentation logic and behavioral data signals.
- • **Recruiting:** Built a resume parsing and candidate scoring workflow; run pre-screen calls and interviews using structured evaluation criteria.
- • **Web scraping:** Build new spiders to extend data coverage; debug and fix bugs in existing scrapers across LinkedIn, Indeed, and ATS platforms.

### 2. Analyst Intern
**De Canaria · Apr 2023 – Jun 2023**

> Three-month intern stint that became the full-time role. Half technical, half business-analyst.
>
- • **Scraping foundations:** Built Reddit scrapers in Selenium + Beautiful Soup; learned Scrapy as the runway to the production pipelines I'd build next.
- • **Business model analysis:** Mapped value propositions, customer segments, and revenue/cost structures of job-posting platforms using the Business Model Canvas; synthesized into platform optimization and go-to-market recommendations.

### ~~3. Salesman · Flo Shoemaking and Merchandising · Apr 2018 – Jun 2019~~

*Removed from LinkedIn. Seven years old, low signal for quant-track recruiters.*

---

## Projects

### Real-Time Stock Market Analyzer · End-to-End Signal Engine
*Jun 2023 – Present*

> Stage 1 of my three-stage quant research pipeline. Polls yfinance for BIST equities and computes 70+ indicators across momentum, trend, volatility, volume, and support/resistance categories. Feeds a live Grafana dashboard and an ML-ready feature schema downstream.
>
- • **Indicator coverage:** RSI, MACD, Ichimoku Cloud, SuperTrend, ATR bands, Fibonacci retracements, Pivot Points (70+ total).
- • **Multi-factor signals:** Cross-indicator consensus logic (e.g., Cloud Position + TK Cross + SuperTrend direction + MFI) reduces false-signal rate vs single-indicator approaches.
- • **Extensibility:** Designed for any yfinance-supported market; BIST is the primary research focus, with US equities and crypto also supported.

### Transaction Cost-Adjusted Backtesting Framework
*Sep 2024 – Present*

> Stage 2 of the pipeline. Backtesting engine with realistic friction modeling. Every strategy is evaluated under tradeable, not theoretical, conditions. Validated against 2 years of historical BIST data; live paper trading bridges in-sample backtesting to out-of-sample reality.
>
- • **Transaction cost modeling:** Fixed-commission cost structure reflecting real broker fees (Ziraat Yatirim Standard, 0.315% round-trip on BIST).
- • **Walk-forward validation:** Rolling out-of-sample evaluation prevents lookahead bias and tests robustness across shifting market regimes.
- • **Risk-adjusted metrics:** Sharpe, CAGR, Max Drawdown, Win Rate, Profit Factor, and average hold period computed for every strategy.

### ML-Driven Strategy Miner · Automated Alpha Discovery Engine
*Jan 2026 – Present*

> Stage 3, the terminal stage of the pipeline. Ensemble-learning system that systematically discovers, ranks, and filters alpha-generating strategies at scale. Feature-space exploration generates ~40 strategy configurations per run from the 70+ indicator universe; XGBoost and Random Forest classify candidates by predictive strength before backtesting.
>
- • **Backtest results:** Top 5 strategies hit 72–74% win rates and Profit Factors of 6.7–9.5 across 90+ BIST tickers *(in-sample backtest)*. Live paper trading is the out-of-sample validation stage where the honest numbers emerge.
- • **Validation discipline:** Every ML-ranked candidate is evaluated under realistic transaction cost assumptions before entering the leaderboard.
- • **Institutional-style workflow:** Three-system pipeline (Real-Time Analyzer → Backtesting Framework → Strategy Miner) replicating an institutional quant research workflow at personal scale.

> **Optional add:** LinkedIn Projects supports a URL field. Link each project to its GitHub repo at github.com/TolgaUyanik for credibility-multiplier effect.

---

## Skills

### Top 3 (pinned · show beside your name in search results)

1. **Quantitative Research**
2. **Algorithmic Trading**
3. **Machine Learning**

### Full list (~35 skills · paste in this order)

**Quant & trading research**
Quantitative Research · Quantitative Analysis · Algorithmic Trading · Backtesting · Walk-Forward Validation · Multi-Factor Modeling · Risk-Adjusted Metrics · Feature Engineering · Time Series Analysis · Statistical Modeling · Technical Indicators

**Machine learning**
Machine Learning · XGBoost · Random Forest · Ensemble Learning · Hidden Markov Models · MLOps · Vertex AI · Feature Space Exploration

**Programming & data**
Python · Pandas · NumPy · SQL · Data Analysis · Data Pipelines · Data Normalization

**Alternative data & scraping**
Alternative Data · Web Scraping · Selenium · Beautiful Soup · Scrapy · Playwright · Unstructured Data Ingestion

**Cloud & infrastructure**
Google Cloud Platform (GCP) · Snowflake · Docker

**Analyst / business**
Competitive Analysis · Feature Gap Analysis · Business Model Canvas

**Reporting & visualization**
Grafana · Power BI · Microsoft Excel

---

## Education

### Gazi University
**Bachelor of Business Administration · Economics**
*Sep 2017 – Jun 2022*

**Relevant coursework:** 
- Mathematical Economics I & II 
- Statistics and Probability I & II 
- Econometrics I & II 
- Research Methods in Economics 
- Financial Management 
- Financial Markets 
- Financial Globalization and Emerging Market Economies

> *GPA omitted (LinkedIn convention for sub-3.5). High school omitted (convention once you have a bachelor's + work experience).*

---

## Certificates

### Keep on LinkedIn (9)

1. **Professional Machine Learning Engineer Study Guide** · Google · Oct 2024
2. **ML Pipelines on Google Cloud** · Google · Nov 2024
3. **Production Machine Learning System** · Google · Jun 2024
4. **Machine Learning Operations (MLOps) Fundamentals** · Google · Oct 2024
5. **Build, Train and Deploy ML Models with Keras on Google Cloud** · Google · May 2024
6. **Preparing for the Google Cloud Professional Data Engineer Exam** · Google · Aug 2023
7. **Scientific Computing with Python** · FreeCodeCamp · Apr 2024
8. **Data Analysis with Python** · FreeCodeCamp · Mar 2023
9. **Business Analysis Fundamentals · ECBA · CCBA · CBAP endorsed** · Udemy · Aug 2023

### Delete from LinkedIn (16)

These are intro-level / low-signal. They dilute the depth signal of the keepers:

- Introduction to AI and Machine Learning on Google Cloud
- Launching into Machine Learning
- Introduction to Generative AI
- Introduction to Large Language Models
- Introduction to Responsible AI
- Applying AI Principles with Google Cloud
- Prompt Design in Vertex AI
- Working with Notebooks in Vertex AI
- Big Data and Machine Learning Fundamentals
- Feature Engineering (Google)
- Machine Learning in the Enterprise
- MLOps for Generative AI
- MLOps with Vertex AI: Model Evaluation
- MS Excel Sıfırdan İleri Seviye Excel Öğren · Udemy
- Power BI Sıfırdan İleri Seviye Uygulamalı Power BI Kursu 2022 · Udemy
- What is Business Analysis · LinkedIn (1-hour course)

> LinkedIn doesn't have a "hide" toggle for certificates; you have to delete them from your profile to remove them from public view.

---

## Languages

Use LinkedIn's **dropdown proficiency levels** (recruiters filter on these):

| Language | Level |
|---|---|
| Turkish | Native or bilingual proficiency |
| English | Professional working proficiency |

> Fix the "Advanceed" typo from your current export.

---

## Awards

*Both Wrestling Silver Medals (Apr 2008, Apr 2009) removed from LinkedIn. They're from age ~13–14 with no professional relevance. The wrestling identity is preserved in **Interests** instead.*

---

## Interests

Wrestling · Cycling · Weight Lifting & Resistance Training · Coffee Brewing · Cinema · Dogs

> Wrestling listed first to retain the personal-history thread.

---

## Volunteer Experience

*Removed from LinkedIn. The "Gazi University · Kitap Bankosu" entry had no description and added no signal.*

---

## Open to Work · banner settings

Configure these in LinkedIn's **Open to Work** feature (the green badge/banner). This replaces the "Open to →" line we explicitly removed from the About text. The native banner is what recruiters actually filter on.

- **Job titles I'm interested in:**
  - Quantitative Analyst
  - Quantitative Researcher
  - Alternative Data Analyst
  - Strategy Analyst
  - Business Analyst (data-driven)
- **Locations:** Remote · Open to relocation globally
- **Job types:** Full-time · Contract *(your call)*
- **Start date:** Immediately *(or your call)*
- **Visibility:** Choose between "Recruiters only" *(private green badge)* or "All LinkedIn members" *(#OpenToWork green photo frame, public)*.

---

## Featured section

Pin to the **Featured** strip (appears directly below About). High-leverage real estate; recruiters who scroll past About often click Featured next.

1. **Personal website:** `tolgauyanik.github.io/PersonalWebsite/`. Single highest-leverage Featured item; gives recruiters a deeper portfolio view.
2. **GitHub profile:** `github.com/TolgaUyanik`
3. *(Optional)* A publicly-linkable Datarade dataset listing if any exists, as proof-of-shipped-product.
4. *(Optional)* A blog post or write-up on the three-stage strategy mining pipeline, if you decide to publish one.

---

## Contact info

- **Email:** uyaniktolga123@gmail.com
- **Phone:** +90 506 693 2422
- **Location:** Antalya, Turkey
- **Website:** tolgauyanik.github.io/PersonalWebsite/
- **GitHub:** github.com/TolgaUyanik

---

## Action checklist (when you're updating LinkedIn live)

- [ ] Replace headline
- [ ] Replace About (run the bold parts through a Unicode-bold converter first)
- [ ] Update De Canaria current role description
- [ ] Update De Canaria intern role description
- [ ] Hide/remove the Flo Salesman role
- [ ] Add/update the three Project entries (with optional GitHub URLs)
- [ ] Re-pin top 3 skills (Quantitative Research · Algorithmic Trading · Machine Learning)
- [ ] Add the remaining ~32 skills, remove anything not in the list
- [ ] Drop GPA from Education; remove high school
- [ ] Delete the 16 low-signal certificates
- [ ] Update Languages to LinkedIn-dropdown levels; fix "Advanceed" typo
- [ ] Remove both Wrestling Silver Medals from Awards
- [ ] Add Interests section (Wrestling first)
- [ ] Remove the Kitap Bankosu volunteer entry
- [ ] Configure Open to Work banner with the listed roles
- [ ] Pin personal website + GitHub to Featured

---

*End of profile content.*
