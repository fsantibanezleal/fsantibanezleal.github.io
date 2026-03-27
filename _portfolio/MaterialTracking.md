---
title: "Real-Time Material Tracking & Blending System"
date: 2022-06-01
excerpt: "Digital twin for ore flow tracking, stockpile management, and blending optimization in mining operations.<br/><img src='/images/projects/material_tracking.svg'>"
collection: portfolio
tags: [digital-twin, optimization, mining, pyspark, kedro, real-time]
---

A **real-time material tracking and blending optimization system** that maintains a digital twin of ore flow from mine pits through conveyors and stockpiles to processing plant inputs.

![Material Tracking](/images/projects/material_tracking.svg)

## The problem

Mining operations extract ore from multiple sources with varying mineral compositions. This ore travels through conveyor networks, accumulates in stockpiles, and must be blended to meet specific processing requirements. Without real-time visibility into material properties at each point in the chain, blending decisions rely on delayed lab results and operator experience, leaving significant optimization potential untapped.

## How it works

The system operates on two synchronized layers:

**Physical layer tracking**: Conveyor-mounted sensors, weightometers, and sampling points feed continuous data about material flow rates and estimated properties. The system maintains a time-resolved model of each stockpile's composition based on accumulation and extraction history.

**Optimization layer**: Given the current state of all stockpiles and the target feed requirements for the processing plant, the system formulates blending as a constrained optimization problem -- minimize deviation from target grade specifications subject to tonnage constraints, equipment availability, and extraction sequence feasibility. The solver simulates blending scenarios and recommends extraction strategies that maximize compliance with target specifications while minimizing operational disruptions.

## Key capabilities

- **Stockpile state estimation** from conveyor data, updated on hourly cycles
- **Segregation modeling**: tracks internal composition gradients within stockpiles
- **Scenario simulation**: evaluates extraction sequences against target blending requirements
- **Mineral traceability**: follows material from pit to plant with property estimates at each node
- **Operational dashboards** for monitoring recommendation adherence and blending compliance

## Architecture

- **Pipeline framework**: Kedro with PySpark for distributed data processing
- **Data storage**: Delta Lake on Databricks for versioned, time-travel-capable data
- **Optimization**: XGBoost-based scenario scoring with constraint satisfaction
- **Deployment**: Dockerized pipelines running hourly (tracking) and every 4 hours (optimization)
- **Multi-division**: Configurable per division with shared core engine components

*This project is part of proprietary corporate work. Source code is not publicly available.*
