---
title: Resource library
parent: Program
nav_order: 4
---

# Resource library
{: .no_toc }

Everything referenced by the modules, in one place, plus a short "later" shelf. Free unless marked
with 💰. The modules say *which parts* to use; this page is the index.

1. TOC
{:toc}

## Books

| Book | Used in | Notes |
| --- | --- | --- |
| *Designing Data-Intensive Applications* — Martin Kleppmann 💰 | M3, M4, M9, M10 | The backbone of the databases and distributed-data modules. Read chapter by chapter as assigned. |
| *Fundamentals of Data Engineering* — Joe Reis, Matt Housley 💰 | M6, M7, M11 | The best map of the data engineering lifecycle. Conceptual, not tool-specific. |
| *The Data Warehouse Toolkit* (3rd ed.) — Ralph Kimball, Margy Ross 💰 | M8 | Dimensional modeling. Chapters 1–4 are essential; the rest are industry case studies to skim. |
| *Database Internals* — Alex Petrov 💰 | M3 (optional) | Part I on storage engines goes deeper than DDIA. |
| *OpenIntro Statistics* (free PDF) | M13 | Solid, free, with exercises. |
| *Practical Statistics for Data Scientists* — Bruce, Bruce, Gedeck 💰 | M13 (optional) | Statistics as practised, in Python and R. |
| *Trustworthy Online Controlled Experiments* — Kohavi, Tang, Xu 💰 | M13 | The A/B testing reference. Chapters 1–5 for this program. |
| *Storytelling with Data* — Cole Nussbaumer Knaflic 💰 | M15, M16 | Short, practical, on chart design and narrative. |
| *Lean Analytics* — Croll, Yoskovitz 💰 | M12 (optional) | Metrics by business model. |
| *Statistics Done Wrong* — Alex Reinhart (free online) | M13 | Catalogue of statistical mistakes; short and memorable. |
| *Python Data Science Handbook* — Jake VanderPlas (free online) | M14 | Reference for NumPy, pandas, Matplotlib. |

## Courses and lecture series

| Resource | Used in |
| --- | --- |
| [CMU 15-445/645 Intro to Database Systems](https://15445.courses.cs.cmu.edu/) — lecture videos and notes | M2, M3, M4 |
| [Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp) (DataTalks.Club) | M6, M7, M9, M10 |
| [dbt Learn: dbt Fundamentals](https://learn.getdbt.com/) | M8 |
| [Mode SQL Tutorial](https://mode.com/sql-tutorial/) | M1 |

## Interactive practice

| Resource | Used in |
| --- | --- |
| [SQLBolt](https://sqlbolt.com/) | M1 |
| [Select Star SQL](https://selectstarsql.com/) | M1 |
| [pgexercises](https://pgexercises.com/) | M1 |
| [SQL Murder Mystery](https://mystery.knightlab.com/) | M1 |
| [Use The Index, Luke!](https://use-the-index-luke.com/) | M3 |
| [Hermitage: testing isolation levels](https://github.com/ept/hermitage) | M4 |
| [Jepsen consistency models](https://jepsen.io/consistency) | M4 |
| [Evan Miller's A/B test sample-size calculator](https://www.evanmiller.org/ab-testing/sample-size.html) | M13 |
| [From Data to Viz](https://www.data-to-viz.com/) | M15 |

## Documentation I should actually read

| Docs | Used in |
| --- | --- |
| [PostgreSQL manual](https://www.postgresql.org/docs/current/) — especially *Indexes*, *Performance Tips*, *Concurrency Control* | M2, M3, M4 |
| [DuckDB documentation](https://duckdb.org/docs/) | M1, M5, M8 |
| [Polars user guide](https://docs.pola.rs/) | M5, M14 |
| [Apache Parquet](https://parquet.apache.org/docs/) | M5 |
| [dlt documentation](https://dlthub.com/docs) | M6 |
| [Apache Airflow documentation](https://airflow.apache.org/docs/) | M7 |
| [Dagster documentation](https://docs.dagster.io/) | M7 (optional) |
| [dbt documentation](https://docs.getdbt.com/) | M8 |
| [PySpark documentation](https://spark.apache.org/docs/latest/api/python/) | M9 |
| [Apache Iceberg](https://iceberg.apache.org/docs/latest/) | M9 |
| [Apache Kafka documentation](https://kafka.apache.org/documentation/) | M10 |
| [Redpanda quickstart](https://docs.redpanda.com/) | M10 |
| [Great Expectations](https://docs.greatexpectations.io/) | M11 |
| [Evidence](https://docs.evidence.dev/) and [Metabase](https://www.metabase.com/docs/) | M15 |

## Datasets

| Dataset | Used in | Why |
| --- | --- | --- |
| [NYC TLC trip records](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) | M5, M9, capstone option | Large, Parquet, monthly partitions; the standard "big enough to hurt" dataset |
| [Olist Brazilian e-commerce](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (Kaggle) | M2, M8, M12, M14 | Multi-table, realistic, great for modeling and analytics |
| [GH Archive](https://www.gharchive.org/) | M6, M10, capstone option | Hourly JSON event stream; good for ingestion and streaming |
| [Open-Meteo API](https://open-meteo.com/) | M6 | Simple free API with no key, for pipeline practice |
| [GTFS feeds](https://gtfs.org/) | capstone option | Public transport schedules; relational and time-based |
| [pgexercises dataset](https://pgexercises.com/gettingstarted.html) | M1 | Small, clean, loads into Postgres |

## The "later" shelf

Not part of v0.1. Candidates for a second version once the fundamentals are solid.

- *Streaming Systems* — Akidau, Chernyak, Lax
- *Data Management at Scale* — Piethein Strengholt (data mesh, governance)
- *Designing Machine Learning Systems* — Chip Huyen (where data engineering meets ML)
- CMU 15-721 Advanced Database Systems
- Snowflake / BigQuery / Databricks free tiers, to see the managed versions of what I built
- Rust or Go for building a small storage engine from scratch
