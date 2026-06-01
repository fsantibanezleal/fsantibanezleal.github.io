---
title: "Finn — Personal Finance & Market Forecasting"
date: 2026-04-30
excerpt: "Market-analytics app: walk-forward-validated forecasting, a full risk battery, cost-aware backtests, FinBERT news sentiment, and LATAM coverage (IPSA + Chile macro).<br/><img src='/images/500x300.png'>"
collection: portfolio
tags: [quant, forecasting, finbert, portfolio, risk, fastapi, plotly]
---

**Finn** is a personal-finance and market-analytics web app: track instruments, build watchlists and portfolios, run forecasts, and review risk — behind a fast, server-rendered UI. What sets it apart is what it refuses to fake.

## The idea

Most quant demos default to US tickers and frictionless backtests. Finn validates forecasts the way they would actually be traded, charges realistic costs, and covers Latin American markets that mainstream tools ignore.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The honest parts:</strong><br/>
walk-forward cross-validation (train on the past, test on the unseen next window) · transaction costs charged in every backtest<br/>
<span style="color:#5a9ac0;font-size:13px;">Plus FinBERT finance-aware news sentiment and first-class LATAM coverage — IPSA universe, Chilean macro, Banco Central de Chile.</span>
</div>

Forecasting (ARIMA/SARIMA, Holt-Winters, GARCH, Random Forest, Gradient Boosting), a full risk battery (Sharpe/Sortino/Calmar, VaR/CVaR, Markowitz / HRP / Black-Litterman / Risk Parity, efficient frontier + Monte Carlo), auth-backed watchlists/portfolios, bilingual ES/EN.

## Technical stack

FastAPI + HTMX + Plotly over a quant stack: pandas, numpy, scipy, statsmodels, scikit-learn, PyPortfolioOpt, arch, hmmlearn.

▶ Live at [finn.fasl-work.com](https://finn.fasl-work.com) · [GitHub](https://github.com/fsantibanezleal/CAOS_WEB_Finn_Forecasts) — *educational demo, not investment advice.*
