---
title: "Phase 4: Capstone"
nav_order: 7
---

# Phase 4 · Capstone
{: .no_toc }

**Time budget:** 4 weeks (32 h) · **Prereqs:** Phases 1–3

1. TOC
{:toc}

## Purpose

One project, start to finish, on a dataset I have not used in the program, that demonstrates
everything: a modelled source, an orchestrated and tested pipeline, a dimensional warehouse, a
dashboard, and an analysis memo with a recommendation. It is public, reproducible, and the thing I
show when someone asks what I can do.

## Constraints

- **New data.** Not Olist. Pick from the options below or propose another with comparable complexity.
- **Everything runs from one command** on a clean machine with Docker and `uv`.
- **Every layer has tests** and the README states what is guaranteed.
- **The analysis answers one real question** and ends in a recommendation with stated uncertainty.
- **Four weeks.** Scope to finish, not to impress. A complete small thing beats an incomplete large one.

## Dataset options

| Option | Why it is interesting | Hard part |
| --- | --- | --- |
| **NYC TLC taxi trips** (plus weather from Open-Meteo and zone shapefiles) | Big, monthly partitions, real seasonality | Volume; joining external context |
| **GH Archive** (GitHub public events) | Streaming-shaped JSON, nested, high volume | Nested schema; choosing a slice |
| **A city's GTFS and GTFS-realtime feed** | Schedules vs actuals; a genuine "late" analysis | Real-time ingestion; time zones |
| **Your own data** (bank exports, fitness tracker, browsing history) | Personal motivation; messy formats | Privacy; small volume |

## Deliverables

1. **Source model.** An ER diagram and constrained schema (or documented raw schema) for the source data. Reuses M2.
2. **Pipeline.** Orchestrated ingestion with idempotent, incremental loads and a documented backfill. Reuses M6, M7. Streaming source optional, if the dataset suits it (M10).
3. **Warehouse.** A dbt project with declared grain, tests, freshness checks, one SCD, docs and lineage. Reuses M8, M11.
4. **Metrics and dashboard.** A metric tree, `METRICS.md`, and a published dashboard. Reuses M12, M15.
5. **Analysis.** An EDA notebook, one experiment or inference with proper uncertainty, and a one-page memo. Reuses M13, M14, M16.
6. **Operations.** `RUNBOOK.md`, a monitoring query, and a postmortem for one real failure encountered during the build. Reuses M11.
7. **Write-up.** A page on this site: what was built, architecture diagram, what I would do differently, and links to everything.

## Suggested plan

| Week | Focus | Exit criterion |
| --- | --- | --- |
| 1 | Choose data, scope the question, model the source, land raw data | Raw data for the full period on disk; schema documented; question written down |
| 2 | Pipeline and warehouse | Orchestrated end-to-end run with tests green |
| 3 | Metrics, dashboard, EDA | Dashboard live; EDA findings listed |
| 4 | Inference, memo, operations, write-up | Everything linked from the capstone page; clean-machine rebuild verified |

## Evaluation rubric

Score myself honestly; anything under 3 is a v0.2 module candidate.

| Area | 1 | 3 | 5 |
| --- | --- | --- | --- |
| Data modeling | Flat tables, no keys | Normalised source, star schema with grain | Plus SCD, conformed dimensions, documented trade-offs |
| Pipeline | Runs once by hand | Scheduled, idempotent, backfillable | Plus incremental, monitored, streaming or CDC where warranted |
| Quality | No tests | Key tests and freshness | Plus contracts, anomaly monitoring, a real postmortem |
| Analysis | Descriptive charts | Hypotheses tested with uncertainty | Plus an experiment design or causal caveats handled well |
| Communication | Notebook only | Memo with recommendation | Plus dashboard people would use; a five-minute talk |
| Reproducibility | Works on my machine | One command on a clean machine | Plus CI that runs the tests |

## Done when

- [ ] Dataset chosen and question written down (week 1).
- [ ] All seven deliverables complete.
- [ ] Clean-machine rebuild verified.
- [ ] Rubric scored with notes.
- [ ] Capstone page published and linked from the [progress tracker](../program/progress.md).
- [ ] A retrospective entry in the log: what v0.2 of this program should change.
