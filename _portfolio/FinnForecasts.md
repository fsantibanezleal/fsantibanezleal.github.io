---
title: "Finn — Personal Finance & Market Forecasting"
date: 2026-04-30
excerpt: "Full-stack market-analytics platform: forecasting with walk-forward validation, a full risk and portfolio battery, cost-aware backtesting, FinBERT news sentiment, and LATAM market coverage.<br/><img src='/images/projects/finn_architecture.svg'>"
collection: portfolio
tags: [quant, forecasting, finbert, portfolio, risk, fastapi, plotly]
---

A **full-stack personal-finance and market-analytics platform**: track instruments, build watchlists and portfolios, run statistical and ML forecasts, review risk, and read finance-aware news sentiment — behind a fast, server-rendered UI. What separates Finn from the average finance dashboard is what it refuses to fake.

## Business impact

Finance tooling tends to split into two camps: polished dashboards with shallow analytics, or powerful quant libraries with no usable interface. Neither serves someone who wants *real* forecasting and risk analysis, *honest* backtesting, and coverage of Latin American markets — which mainstream tools largely ignore — without standing up a research environment from scratch. Finn packages a research-grade analytics stack behind a clean web app, and its credibility comes from two deliberate engineering choices most demos skip: forecasts validated the way they would actually be traded, and backtests that charge the costs of trading.

| Metric | Result |
|--------|--------|
| Forecasting models | ARIMA/SARIMA, Holt-Winters, GARCH, Random Forest, Gradient Boosting + HMM regimes |
| Validation | Walk-forward cross-validation (no future leakage) |
| Backtesting | Transaction-cost-aware (`cost_bp`) — net, not gross, equity |
| Market coverage | US + **LATAM** (IPSA universe, Chilean macro, Banco Central de Chile) |
| News sentiment | FinBERT (finance-tuned), not a general sentiment model |

## Strategic context

A quant demo that defaults to US tickers and frictionless backtests looks impressive and quietly misleads — strategies that only worked because they traded for free, and accuracy numbers inflated by future leakage. Finn is built to be the opposite: a tool you could hand to an analyst because it is honest about validation and costs, and relevant because it covers the markets it was built in. As a portfolio piece it demonstrates depth across time-series econometrics, portfolio optimization, NLP, and full-stack delivery — and the judgment to know which guarantees actually make a market tool trustworthy.

![Architecture and integrity guarantees](/images/projects/finn_architecture.svg)

## Key Performance Indicators — what makes it trustworthy

The headline isn't a return number — it's the integrity of the analytics behind every screen.

| KPI | Baseline (typical demo) | With Finn | Impact |
|-----|-------------------------|-----------|--------|
| Forecast validation | In-sample fit (future leaks in) | Walk-forward cross-validation | Reported error is genuinely out-of-sample |
| Backtest realism | Zero-cost trades | Transaction costs charged (`cost_bp`) | Strategies must survive contact with reality |
| News sentiment | General-purpose model | FinBERT finance-tuned | "missed guidance" vs "raised guidance" read correctly |
| Market coverage | US tickers only | IPSA + Chile macro + BCCh | Usable for Latin American markets |
| State | Stateless toy | Auth-backed watchlists & portfolios | Persisted, multi-instrument workflows |

## The challenge

Bringing research-grade quantitative finance to a responsive web app means three problems at once: a heavy numerical stack (pandas, NumPy, SciPy, statsmodels, PyPortfolioOpt, arch, hmmlearn) that must answer fast; methodological rigor that resists the usual demo shortcuts; and a UI that stays snappy while rendering econometric charts. Finn solves the speed/weight tension with a server-rendered HTMX architecture and cached computation, and solves the rigor problem head-on: **walk-forward cross-validation** trains on the past and tests on the unseen next window (rolling forward, never leaking the future into the fit), and the backtester charges **transaction costs**, the fastest way to kill a strategy that only looked good because it traded for free.

## System architecture

1. **Data layer**: market OHLCV via yfinance, fundamentals, an 8-source financial news RSS aggregator, and macro series from FRED — plus a first-class **LATAM** extension (IPSA universe, Chilean macro series, a Banco Central de Chile stub).
2. **Analytics core (FastAPI)**: a quant stack exposed as cached endpoints — forecasting (ARIMA/SARIMA, Holt-Winters, GARCH, RF, Gradient Boosting; HMM regime detection), a full risk battery (volatility, Sharpe/Sortino/Calmar, VaR/CVaR), and portfolio optimization (Markowitz, HRP, Black-Litterman, Risk Parity, efficient frontier + Monte Carlo).
3. **Sentiment**: FinBERT scores headlines via the HF Inference API and folds finance-aware sentiment into the view.
4. **Backtesting**: Buy & Hold, periodic rebalancing, momentum, mean-reversion and pairs strategies — each evaluated with transaction costs and the full risk metric suite, reporting net equity and drawdown.
5. **Frontend & persistence**: Jinja2 + HTMX server rendering with interactive Plotly charts (fan charts, drawdown, fundamentals bubbles, regime shading); auth-backed watchlists and portfolios persist per user; bilingual ES/EN.

## Technology stack

- **Backend**: FastAPI, Pydantic v2, Uvicorn; SQLAlchemy persistence + auth
- **Quant**: pandas, NumPy, SciPy, statsmodels, scikit-learn, PyPortfolioOpt, arch, hmmlearn
- **Data**: yfinance, FRED / pandas-datareader, feedparser; FinBERT via HF Inference API
- **Frontend**: Jinja2, HTMX, Plotly.js, custom dark-theme CSS
- **Deployment**: systemd + nginx on a Hetzner VPS

## Live application

▶ **[Live demo — finn.fasl-work.com](https://finn.fasl-work.com)** — forecasting, risk, portfolios, and news sentiment in one app.

[View on GitHub](https://github.com/fsantibanezleal/CAOS_WEB_Finn_Forecasts)

*Educational demonstration — not financial advice, investment recommendation, or an offer to buy or sell.*
