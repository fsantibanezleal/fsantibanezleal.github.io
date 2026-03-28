---
title: 'Week in review: From developer portfolios to executive narratives'
date: 2026-03-28
permalink: /posts/2026/03/week-executive-reframing/
tags:
  - portfolio
  - management
  - career
  - week-in-review
---

This week's biggest change wasn't technical -- it was narrative. I restructured six industry portfolio entries to lead with business impact instead of algorithms. The shift reflects a real career evolution: from implementing models to owning their business outcomes.

## The reframing

For years, my portfolio entries opened with architecture diagrams, framework choices, and model specifications. That made sense when I was the person writing the code. But the audience for a portfolio isn't other developers -- it's decision-makers evaluating whether you can deliver results. So this week I rewrote the entries to open with KPI tables and strategic context before diving into technical details. Every project now starts with the question a VP would ask: "What did this do for the operation?"

![Mining optimization pipeline](/images/projects/mining_optimization.svg)

## The numbers that matter

The difference is subtle but important. Saying "+100 TPH throughput gain via XGBoost ensemble" is a developer's summary. Saying "+100 TPH throughput gain, translating to approximately USD 8-12M in additional annual revenue at current copper prices" is how the business sees it. Similarly, "15% reduction in environmental alerts" sounds like a model metric, but what it actually means is operational continuity -- a mine that consistently violates environmental regulations can be shut down, and the regulatory exposure alone dwarfs the cost of the monitoring system.

<div class="equation-card" markdown="1">

**Return on Investment**

$$\text{ROI} = \frac{\text{TPH}_{gain} \times \text{hours}_{year} \times \text{copper\_price} \times \text{recovery}}{\text{project\_cost}}$$

</div>

The equation above is one I now include in executive summaries. It connects the model output directly to the financial outcome, which is ultimately what justifies the investment in data science infrastructure.

## Developer to Technical Lead to Manager

Looking at the same projects through different lenses is a strange experience. When I built the throughput optimizer, I was proud of the feature engineering pipeline and the Kedro orchestration. When I led the team extending it, I was focused on code quality, testing coverage, and deployment reliability. Now, as the person accountable for the outcome, I think about whether the gain holds quarter over quarter, whether the operations team actually trusts the recommendations, and whether the ROI justifies expanding the approach to other plants. The same project, three completely different narratives -- all of them true.

This reframing isn't just cosmetic. It changes how you think about what to build next. When your mental model starts with the business outcome and works backward to the technical solution, you make different architectural decisions. You prioritize differently. You communicate differently.

Beyond the portfolio rewrite, this was also a productive week for the website itself: added 9 frontend screenshots, embedded 3 YouTube demo videos, and enriched 20+ rolling entries with SVGs and equations. The website is becoming a living technical portfolio -- not just a list of projects, but a record of how my perspective on those projects has evolved over time.
