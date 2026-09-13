---
title: Principles
parent: Program
nav_order: 2
---

# Principles
{: .no_toc }

The learning-design decisions behind the program, so that future edits stay consistent.

1. TOC
{:toc}

## Projects over tutorials

Every module ends with a build. Tutorials produce the feeling of understanding; a project that
does not work yet produces understanding. The resource lists are deliberately short so that
the majority of time goes to practice and building.

## Retrieval over rereading

The *Check yourself* questions are meant to be answered from memory, out loud or in writing,
before looking anything up. Rereading notes is the least effective use of study time; testing
myself is the most effective. The weekly review session exists for this.

## One stack, deep

The program standardises on one stack so that tooling never becomes the lesson:

| Layer | Choice | Why |
| --- | --- | --- |
| Relational database | PostgreSQL | Industry default, best documentation, exposes internals well |
| Analytical engine | DuckDB | Zero setup, fast, reads Parquet and CSV directly |
| Language | Python 3.12+ with `uv` | Ubiquitous in data; `uv` removes environment pain |
| Dataframes | Polars (pandas for reading other people's code) | Fast, explicit, good docs |
| Transformation | dbt | The standard for analytics engineering |
| Orchestration | Airflow (Dagster as optional alternative) | Most common in job descriptions |
| Visualization | Plotly and Evidence or Metabase | Interactive charts; a real dashboard tool |
| Environment | Docker Compose | Reproducible services (Postgres, Airflow, Kafka) |

Breadth comes from reading (DDIA, Fundamentals of Data Engineering), not from installing
every tool once.

## Ship something every module

Each build produces an artefact that lives in git: a schema, a pipeline, a notebook, a chart, a
memo. The capstone stitches these together, so sloppy builds create work later.

## Write to think

Notes are written in my own words, not copied. The learning log records what was hard and what
I would do differently. Both are public on this site, which is a mild but useful pressure.

## Time-box, then decide

Module budgets are estimates. Overrunning is information, not failure. The rule is to notice it
(the log), name the cause, and choose deliberately: cut, split, or continue.

## Fundamentals age slowly

The program spends more time on relational theory, storage, transactions, dimensional
modeling and statistics than on any specific tool. Tools will change within a year; the
fundamentals will not.
