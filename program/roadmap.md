---
title: Roadmap
parent: Program
nav_order: 1
---

# Roadmap
{: .no_toc }

1. TOC
{:toc}

## Shape of the program

```
Phase 0  Setup ─┐
                ▼
Phase 1  Databases (M1–M4) ───────────────┐
                                          ▼
Phase 2  Data engineering (M5–M11) ◄────► Phase 3  Data analytics (M12–M16)
                                          │
                                          ▼
Phase 4  Capstone
```

Phase 1 is the foundation and comes first: SQL and relational thinking are used in every later
module. Phases 2 and 3 are independent of each other and can be interleaved. Phase 4 assumes both.

## Default schedule (8 h/week)

| Week | Module |
| --- | --- |
| 1 | [Phase 0 · Setup](../tracks/00-setup.md) |
| 2–3 | [M1 · SQL fundamentals](../tracks/databases/01-sql-fundamentals.md) |
| 4–5 | [M2 · Data modeling and schema design](../tracks/databases/02-data-modeling.md) |
| 6–7 | [M3 · Storage, indexes and query plans](../tracks/databases/03-storage-and-indexes.md) |
| 8 | [M4 · Transactions and concurrency](../tracks/databases/04-transactions.md) |
| 9 | [M5 · Python, files and formats](../tracks/data-engineering/05-files-and-formats.md) |
| 10–11 | [M6 · Ingestion and batch pipelines](../tracks/data-engineering/06-ingestion-and-pipelines.md) |
| 12 | [M7 · Orchestration](../tracks/data-engineering/07-orchestration.md) |
| 13–14 | [M8 · Warehousing and analytics engineering](../tracks/data-engineering/08-warehousing-and-dbt.md) |
| 15 | [M9 · Distributed data and the lakehouse](../tracks/data-engineering/09-distributed-data.md) |
| 16 | [M10 · Streaming basics](../tracks/data-engineering/10-streaming.md) |
| 17 | [M11 · Data quality and operations](../tracks/data-engineering/11-quality-and-ops.md) |
| 18 | [M12 · Analytical thinking and metrics](../tracks/analytics/12-metrics.md) |
| 19–20 | [M13 · Statistics for analysts](../tracks/analytics/13-statistics.md) |
| 21 | [M14 · Exploratory data analysis](../tracks/analytics/14-eda.md) |
| 22 | [M15 · Visualization and dashboards](../tracks/analytics/15-visualization.md) |
| 23 | [M16 · Communicating analysis](../tracks/analytics/16-communication.md) |
| 24–27 | [Phase 4 · Capstone](../capstone/index.md) |

## Weekly rhythm

Eight hours split into five sessions. The split matters more than the total: without the practice
and build sessions, study alone produces recognition, not skill.

| Session | Length | What |
| --- | --- | --- |
| Study ×2 | 1.5 h each | Read or watch the module's *Study* material. Take notes in my own words. |
| Practice ×2 | 1.5 h each | The module's *Practice* exercises. No notes open unless stuck for 15 minutes. |
| Build ×1 | 1.5 h | Work on the module's *Build* project. |
| Review | 0.5 h | Answer *Check yourself* from memory, update [progress](progress.md), write the [log](../log/index.md) entry. |

## Rules for moving on

- A module is done when every item in its **Done when** list is ticked, not when the resources are consumed.
- If a module takes twice its budget, stop and write down why in the log. Then either cut scope (drop the optional items) or split it.
- Skipping a module is allowed if I can pass its *Check yourself* questions cold. Write that down too.

## Adjusting the plan

- **Less time** (4 h/week): keep the same modules, double the calendar. Do not drop the build sessions.
- **More time** (15 h/week): run Phase 2 and Phase 3 modules in parallel (one of each per week).
- **Already know SQL**: do M1's *Check yourself*; if it is easy, do only its *Build* and move to M2.
- **Job pressure toward one track**: after Phase 1, do that whole phase first, then the other.

## What "done" looks like

After Phase 1 I can design a normalised schema, write window-function SQL fluently, read an
`EXPLAIN` plan, and explain isolation levels with examples I have reproduced.

After Phase 2 I can build a scheduled, idempotent pipeline from a source system into a dimensional
warehouse modelled with dbt, with tests, and explain when I would reach for Spark, a lakehouse table
format, or a streaming system.

After Phase 3 I can define metrics that survive scrutiny, run and interpret an A/B test, do an EDA
that finds the real story in a dataset, and present it in a chart and a one-page memo.

After Phase 4 I have one public project that demonstrates all of the above.
