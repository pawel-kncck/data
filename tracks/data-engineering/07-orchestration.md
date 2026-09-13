---
title: "M7 · Orchestration"
parent: "Phase 2: Data engineering"
nav_order: 3
---

# M7 · Orchestration
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** M6

1. TOC
{:toc}

## Why this matters

A pipeline nobody runs is a script. Orchestration is the layer that runs it on a schedule,
retries the right things, backfills history, and tells me when it fails. Airflow is the tool
most job descriptions name; the concepts (DAGs, scheduling intervals, idempotent tasks, backfills)
transfer to every alternative.

## Learning outcomes

By the end I can:

- explain a DAG, a task, a run, a schedule interval and the difference between logical date and run time;
- run Airflow locally with Docker Compose and write a DAG that runs the M6 pipeline;
- configure retries, timeouts, SLAs, and alerting on failure;
- backfill a date range and explain why tasks must be idempotent for that to be safe;
- pass data between tasks correctly (small metadata via XCom; real data via storage) and explain why;
- compare Airflow's task-centric model with Dagster's asset-centric model.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| [Airflow docs: Core Concepts](https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/index.html) | DAGs, Tasks, Operators, DAG Runs, XComs, and *the logical date* section. | 2 h |
| [Airflow docs: Running Airflow in Docker](https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html) | Follow it. | 1 h |
| Data Engineering Zoomcamp, week 2 (orchestration) | Watch. The Zoomcamp uses a different tool some years; the concepts are the same. | 1.5 h |
| *Fundamentals of Data Engineering* chapter 2 (the *Orchestration* undercurrent) | Read the section. | 0.5 h |
| [Dagster: Concepts, Assets](https://docs.dagster.io/) (optional) | Read the asset model overview; note what Airflow makes hard that this makes easy. | 0.5 h |

## Practice

1. Start Airflow via Compose. Write a DAG for the weather pipeline from M6 with three tasks: extract → load → validate row counts. Schedule it daily. Set retries to 3 with exponential backoff.
2. Make the extract task use the DAG run's logical date rather than "today". Backfill the last 14 days with the CLI and verify no duplicates.
3. Break the load task on purpose (bad credentials). Watch the retries, the failure, and configure an on-failure callback that writes to a log or a local webhook.
4. Add the Olist database ingestion as a second DAG and make the dbt placeholder task (to be filled in M8) depend on both via a dataset or an external task sensor.

## Build

**The pipeline, v2: scheduled.** Extend `projects/pipeline/` with `dags/`, the Compose file for
Airflow, and a README section that explains: the schedule, what happens on failure, how to
backfill, and why each task is safe to re-run. Screenshot the DAG graph and the backfill grid
for the site.

## Check yourself

- A daily DAG scheduled at `0 2 * * *` has a run with logical date 2024-03-10. When does it actually execute, and what data interval should the extract task read?
- Why is passing a dataframe through XCom a bad idea?
- What makes a task safe to retry? Give one example of a task that is not.
- What is a backfill, and what could go wrong if the loader appends?
- What is the difference between a sensor and a dependency?
- In one paragraph: what does an asset-centric orchestrator change about how I write pipelines?

## Done when

- [ ] Airflow runs locally; the weather DAG succeeds on schedule.
- [ ] Logical-date-driven extraction and a 14-day backfill without duplicates.
- [ ] Failure path exercised: retries, failure, callback.
- [ ] Two DAGs with a cross-DAG dependency.
- [ ] `projects/pipeline/` v2 documented with screenshots.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m07-orchestration.md` once written._
