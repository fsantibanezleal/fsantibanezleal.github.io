---
title: "Real-Time Material Tracking & Blending System"
date: 2022-06-01
excerpt: "Digital twin for ore flow tracking, stockpile management, and blending optimization in mining operations.<br/><img src='/images/projects/material_tracking.svg'>"
collection: portfolio
tags: [digital-twin, optimization, mining, pyspark, kedro, real-time]
---

A **real-time material tracking and blending optimization system** that maintains a digital twin of ore flow from mine pits through conveyors and stockpiles to processing plant inputs.

## Business impact

This system created real-time visibility into ore flow that simply did not exist before — closing a critical information gap between mine extraction and plant processing. Blending compliance improved significantly, reducing out-of-spec feed to the processing plant and enabling proactive stockpile management that maintains operational continuity across shifts and planning horizons.

| Metric | Result |
|--------|--------|
| Tracking cycle | Hourly updates |
| Optimization | Every 4 hours |
| Feed compliance | Improved blending adherence |
| Deployment | Configurable multi-division |

## Strategic context

Without material tracking, blending decisions relied on delayed lab results — hours to days old — and individual operator experience. This system closed that gap, giving operators real-time visibility to make blending decisions that directly affect processing efficiency and product quality. The configurable multi-division architecture ensured that each operation could adapt the system to its specific ore body and logistics constraints.

![Material Tracking](/images/projects/material_tracking.svg)

## Key Performance Indicators — Process impact

The system closes the information gap between ore extraction and processing, enabling blending decisions based on current state rather than historical assumptions.

| KPI | Baseline | With system | Impact |
|-----|----------|-------------|--------|
| Blending visibility | Delayed lab results (hours to days) | Real-time stockpile state estimation | Decisions based on current ore properties |
| Feed compliance | Reactive correction after off-spec events | Proactive blending optimization | Reduced out-of-specification feed to plant |
| Tracking granularity | Batch-level estimates | Hourly conveyor-level tracking | Fine-grained material flow visibility |
| Decision cadence | Shift-based manual assessment | Hourly tracking, 4-hourly optimization | Continuous improvement loop |

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
