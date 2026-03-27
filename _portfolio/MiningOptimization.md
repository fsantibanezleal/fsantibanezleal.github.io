---
title: "Mining Process Optimization Platform"
date: 2022-01-01
excerpt: "End-to-end ML platform for optimizing SAG milling, flotation, and thickening operations across multiple mining divisions.<br/><img src='/images/projects/mining_optimization.svg'>"
collection: portfolio
tags: [machine-learning, mining, optimization, kedro, azure, mlops]
---

An **end-to-end machine learning platform** for optimizing mineral processing operations — SAG milling, flotation, and thickening — deployed across multiple mining divisions and processing plants.

![Pipeline Architecture](/images/projects/mining_optimization.svg)

## The challenge

Large-scale mining operations involve complex, interconnected processes where small improvements in throughput or recovery translate into significant economic impact. SAG mills, flotation banks, and thickeners each have dozens of controllable variables and hundreds of sensor readings, creating a high-dimensional optimization problem that evolves continuously with ore characteristics.

## System architecture

The platform follows a modular pipeline architecture built on Kedro for reproducibility and MLOps best practices:

1. **Data ingestion**: Streaming and batch pipelines pulling from SCADA systems, lab analyses, and operational databases via Azure Data Factory
2. **Feature engineering**: Domain-informed features including rolling statistics (mean, variance, percentiles over configurable time windows), lag variables capturing process inertia, ore property indicators derived from assay data, and operational regime detection via hidden Markov models or change-point algorithms
3. **Model training**: Ensemble of XGBoost, gradient-boosted trees, and neural networks trained on historical operational windows
4. **Recommendation engine**: Scenario simulation generating actionable setpoint recommendations with confidence intervals
5. **Operational dashboard**: Real-time monitoring of adherence to recommendations, KPI tracking, and expert feedback loops

## Results

- Throughput uplift scenarios exceeding **+100 TPH** in SAG milling operations
- Measurable improvements in **copper recovery** across flotation circuits
- **Hourly tracking cycles** with 4-hourly optimization recommendations in production
- Multi-division deployment with division-specific parameter tuning

## Technology stack

- **Orchestration**: Kedro pipelines with Azure Databricks execution
- **Compute**: PySpark for distributed processing, Delta Lake for data storage
- **ML**: XGBoost, scikit-learn, with MLflow experiment tracking
- **Infrastructure**: Docker containers on Azure Container Registry, CI/CD via Azure Pipelines
- **Visualization**: Power BI dashboards with Streamlit prototypes for model exploration

*This project is part of proprietary corporate work. Source code is not publicly available.*
