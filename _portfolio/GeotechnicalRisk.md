---
title: "Geotechnical Risk Prediction System"
date: 2023-06-01
excerpt: "ML-based prediction of geotechnical hazards in underground mining using seismic data, spatial features, and 3D block models.<br/><img src='/images/projects/geotechnical_risk.svg'>"
collection: portfolio
tags: [machine-learning, geotechnical, mining, seismic, risk-prediction, xgboost]
---

A **machine learning system for predicting geotechnical hazards** — including rockburst and slope instability events — in underground and open-pit mining operations.

## Business impact

This system replaced ad hoc manual expert judgment with systematic, data-driven risk assessment on a weekly operational cadence. It enables access restriction decisions that balance safety with productivity — each unnecessary closure costs production tonnage, while each missed hazard risks lives and equipment. Interpretable outputs (SHAP-based feature importance) ensure that geologists and mine planners trust and act on the predictions.

| Metric | Result |
|--------|--------|
| Assessment frequency | Weekly |
| Risk levels | Green / Amber / Red (traffic-light system) |
| Explainability | SHAP feature importance per prediction |
| Integration | Operational planning systems |

## Strategic context

Underground mining safety decisions traditionally depend on individual expert judgment, which varies across shifts, geologists, and sites. This system provides a consistent, data-driven baseline that supports — not replaces — expert decisions, ensuring that risk assessment is systematic and auditable. For mining operations, the ability to demonstrate a rigorous, repeatable safety process is both an operational necessity and a regulatory expectation.

![Geotechnical Risk](/images/projects/geotechnical_risk.svg)

## Key Performance Indicators — Process impact

The system shifts geotechnical risk management from reactive expert judgment to proactive data-informed planning, with quantifiable detection capabilities.

| KPI | Baseline (manual) | With system | Impact |
|-----|-------------------|-------------|--------|
| Detection capability | Expert-dependent, inconsistent | >80% detection of critical geophysical event patterns | Systematic, auditable risk assessment |
| Short-term decision support | Post-event response | Pre-event area isolation timing evaluation | Proactive safety management |
| Medium-term planning | Not systematically addressed | Production plan adjustment for projected gradual phenomena (pillar collapse) | Risk-informed mine planning |
| Assessment cadence | Irregular, event-triggered | Weekly systematic evaluation | Consistent operational rhythm |

## The challenge

Underground mining operations face inherent geotechnical risks. Rock mass under stress can fail suddenly, creating hazards for equipment and personnel. Traditional assessment relies on manual geological surveys and rule-of-thumb thresholds applied to seismic monitoring data. These approaches miss complex spatial and temporal patterns that precede major events.

## Approach

The system transforms raw seismic monitoring data into actionable risk predictions through a multi-stage pipeline:

### Feature engineering
Raw seismic event catalogs are transformed into meaningful indicators:
- **Energy indices**: cumulative seismic energy release, apparent stress (ratio of seismic energy to seismic moment), and windowed energy rate patterns
- **Spatial features**: event clustering (DBSCAN-based), migration velocity vectors, proximity to mapped geological structures and excavation faces
- **Temporal patterns**: event rate changes, seismic quiescence detection, Gutenberg-Richter b-value estimation from frequency-magnitude distributions
- **Block model integration**: geological and geomechanical properties from 3D mine models

### Classification
Ensemble ML models (XGBoost with SHAP explainability) classify spatial blocks into risk levels, providing both predictions and interpretable feature importance for each assessment. Geologists can understand *why* a zone is flagged, not just that it is.

### Operational integration
Risk predictions feed into operational planning systems, informing decisions about:
- **Access restrictions** for high-risk zones
- **Blasting sequence optimization** to manage induced seismicity
- **Support design** recommendations based on predicted stress conditions

## Technology stack

- **Pipeline**: Kedro 1.0 with Databricks Asset Bundles for deployment
- **ML**: XGBoost with SHAP explanations, scikit-learn preprocessing
- **Data**: PySpark + Delta Lake with Unity Catalog governance
- **Deployment**: Multi-environment (dev/preprod/prod) with CI/CD
- **Output**: JSON risk assessments consumed by operational planning systems

*This project is part of proprietary corporate work. Source code is not publicly available.*
