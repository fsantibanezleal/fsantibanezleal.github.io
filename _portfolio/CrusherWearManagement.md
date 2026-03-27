---
title: "Crusher Liner Wear Management System"
date: 2025-09-01
excerpt: "Full-stack platform for 3D point cloud analysis, wear profile tracking, and remaining-life forecasting of industrial crusher liners.<br/><img src='/images/projects/crusher_wear_system.svg'>"
collection: portfolio
tags: [point-cloud, 3d-analysis, wear-forecasting, fastapi, nextjs, python]
---

A **full-stack platform** for tracking and forecasting the wear of crusher liners in minerals processing operations, built from raw 3D laser scan data through to production deployment.

![Architecture](/images/projects/crusher_wear_system.svg)

## The challenge

Gyratory and cone crushers are among the largest and most critical machines in a minerals processing plant. Their concave and mantle liners degrade continuously under extreme loads, and knowing when to schedule a liner change is a costly decision: too early wastes material, too late risks catastrophic failure. Traditionally, wear is estimated with manual caliper measurements taken during maintenance windows -- a slow, imprecise, and sometimes dangerous process. 3D laser scanning offers a far richer picture, but the raw point clouds (millions of points in DXF or PTS format) require significant processing before they become actionable.

## System architecture

1. **Point cloud ingestion and parsing**: Raw scan files (DXF, PTS) are parsed and transformed into cylindrical coordinate representations aligned to the crusher axis. Aggregation routines collapse the dense point cloud into interpretable radial-axial wear profiles.
2. **Campaign and survey management**: Each crusher liner installation defines a campaign. Multiple surveys (scans) are registered within a campaign, enabling wear progression tracking over time. The system manages metadata, alignment corrections, and reference geometries.
3. **Wear trend modeling and forecasting**: Wear rates are computed per profile zone, and regression models project remaining useful life. The system generates recommended change dates with confidence bounds, supporting maintenance planning.
4. **Dual deployment architecture**: The platform operates in two modes. A **desktop application** (Streamlit/Dash packaged with PyInstaller) serves offline mine sites with no internet connectivity. A **web platform** (Next.js frontend, FastAPI backend, PostgreSQL database, Redis caching) provides centralized management for multi-site operations.
5. **Infrastructure**: Docker Swarm orchestration with Traefik as reverse proxy and load balancer. Ansible playbooks automate provisioning and deployment across environments.

## Technology stack

- **Backend**: FastAPI (Python), PostgreSQL, Redis, Celery for async tasks
- **Frontend**: Next.js (React/TypeScript)
- **Desktop**: Streamlit and Dash applications, packaged via PyInstaller
- **3D Processing**: NumPy, SciPy, Open3D for point cloud manipulation
- **Infrastructure**: Docker Swarm, Traefik, Ansible, Nginx
- **ML/Forecasting**: scikit-learn, custom regression models for wear projection

*Note: This description reflects the general type and architecture of systems I have built as a consultant for a mining equipment services company. Specific client details, operational data, and proprietary methodologies are omitted.*
