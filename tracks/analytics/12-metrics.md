---
title: "M12 · Analytical thinking and metrics"
parent: "Phase 3: Data analytics"
nav_order: 1
---

# M12 · Analytical thinking and metrics
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** M1

1. TOC
{:toc}

## Why this matters

Most analytical failures happen before any query is written: the wrong question, a metric that
does not measure what people think it measures, or a "conversion rate" whose numerator and
denominator nobody agreed on. This module is about turning vague business questions into precise,
answerable ones and defining metrics that stay meaningful when the business changes.

## Learning outcomes

By the end I can:

- reframe a vague request ("why are sales down?") into a hierarchy of specific, testable questions;
- build a metric tree from a north-star metric down to input metrics, and identify which are actionable;
- write a metric definition (numerator, denominator, grain, filters, time window, edge cases) precise enough to implement;
- compute and interpret standard e-commerce and product metrics: conversion, AOV, retention and cohort curves, churn, LTV, funnel drop-off;
- recognise common metric traps: ratio-of-averages vs average-of-ratios, survivorship, mix shift, Goodhart's law;
- decide what a metric's movement *cannot* tell me and what analysis would.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| [Amplitude: North Star Playbook](https://amplitude.com/north-star) (free) | Read; build one metric tree while reading. | 1.5 h |
| [Lenny's Newsletter / Reforge-style writing on metric trees](https://www.lennysnewsletter.com/) | Pick two pieces on metrics and input metrics. | 1 h |
| *Lean Analytics* chapters 2–5 (optional) | Metric types and "one metric that matters". | 1.5 h |
| [Sequoia: Retention](https://www.sequoiacap.com/article/retention/) and the cohort-analysis explainer of your choice | Read; sketch a cohort table by hand. | 1 h |
| A blog post on Simpson's paradox with a real business example | Read and explain it back in one paragraph. | 0.5 h |

## Practice

1. Take three vague questions about Olist ("are we growing?", "which sellers are good?", "is delivery a problem?") and decompose each into a question tree with at least three levels, ending in queries I could write.
2. Build the Olist metric tree: north-star (for example, delivered order value) → inputs (orders, AOV, delivery success) → drivers. Mark which are actionable by which team.
3. Write full definitions for five metrics: repeat-purchase rate, late-delivery rate, review score, revenue per seller, and monthly active customers. Implement each as a SQL view on the M8 marts (or the raw tables). Find one edge case each that the naive version gets wrong.
4. Build monthly acquisition cohorts and a retention curve for Olist customers. Explain why the curve looks the way it does (hint: the dataset's shape).
5. Find an instance of mix shift in the data: an overall metric moving in the opposite direction from every segment.

## Build

**Olist metrics layer.** `projects/analytics/metrics/`: the metric tree as a diagram, a
`METRICS.md` with the five definitions in a fixed template (name, question it answers,
numerator, denominator, grain, filters, window, edge cases, owner), the SQL views implementing
them, and a one-page "what this metric cannot tell you" note for the north-star.

## Check yourself

- Write the definition template from memory and fill it in for conversion rate.
- What is the difference between average order value computed as `SUM(revenue)/COUNT(orders)` and `AVG(order_revenue)`? When do they differ?
- Explain Simpson's paradox with an example. What question do I ask when I see a metric move?
- What is the difference between a cohort and a segment?
- Why is a north-star metric that a team can not influence a bad north-star for that team?
- What is Goodhart's law and give a data-team example.

## Done when

- [ ] Three question trees written.
- [ ] Metric tree for Olist drawn and annotated.
- [ ] Five metric definitions written and implemented as views with edge cases noted.
- [ ] Cohort retention curve built and explained.
- [ ] One mix-shift example found and explained.
- [ ] `projects/analytics/metrics/` complete.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m12-metrics.md` once written._
