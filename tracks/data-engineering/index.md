---
title: "Phase 2: Data engineering"
nav_order: 5
has_children: true
---

# Phase 2 · Data engineering
{: .no_toc }

**Time budget:** 9 weeks · **Prereqs:** [Phase 1](../databases/index.md)

Moving data reliably from where it is produced to where it is useful. The seven modules follow the
data engineering lifecycle: files and formats, ingestion, orchestration, warehousing and
transformation, distributed processing, streaming, and finally quality and operations. By the end
of the phase one pipeline runs on a schedule, loads into a dimensional warehouse, is tested, and
has been extended with a streaming source.

| Module | Weeks | Outcome |
| --- | --- | --- |
| [M5 · Python, files and formats](05-files-and-formats.md) | 1 | Choose and use CSV, JSON, Parquet correctly; benchmark them |
| [M6 · Ingestion and batch pipelines](06-ingestion-and-pipelines.md) | 2 | Idempotent, incremental loads from an API and a database |
| [M7 · Orchestration](07-orchestration.md) | 1 | The pipeline runs on a schedule with retries and backfills |
| [M8 · Warehousing and analytics engineering](08-warehousing-and-dbt.md) | 2 | A dimensional model built and tested with dbt |
| [M9 · Distributed data and the lakehouse](09-distributed-data.md) | 1 | Know when and how to reach for Spark and Iceberg |
| [M10 · Streaming basics](10-streaming.md) | 1 | Kafka concepts and a working producer/consumer |
| [M11 · Data quality and operations](11-quality-and-ops.md) | 1 | Tests, contracts, monitoring and a runbook |

**Stack:** Python with `uv`, Polars, DuckDB, PostgreSQL, dlt, Airflow, dbt, PySpark (local), Redpanda, Docker Compose.

**Backbone reading:** *Fundamentals of Data Engineering* and *DDIA* chapters 5, 6, 10 and 11; the Data Engineering Zoomcamp for hands-on material.
