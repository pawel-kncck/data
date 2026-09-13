---
title: "M6 · Ingestion and batch pipelines"
parent: "Phase 2: Data engineering"
nav_order: 2
---

# M6 · Ingestion and batch pipelines
{: .no_toc }

**Time budget:** 2 weeks (16 h) · **Prereqs:** M5

1. TOC
{:toc}

## Why this matters

Ingestion is where pipelines actually break: APIs paginate and rate-limit, sources change
schema, runs fail halfway and get retried. The difference between a script and a pipeline is
that a pipeline can be re-run safely. This module builds that reflex, and the pipeline built here
is the one scheduled in M7, modelled in M8 and tested in M11.

## Learning outcomes

By the end I can:

- explain ETL vs ELT and where transformation belongs today, and why;
- design an idempotent load (upsert, delete-insert by partition, or append with dedup) and explain the trade-offs;
- implement incremental extraction with a cursor or watermark, and handle late-arriving data;
- structure a pipeline as extract → land raw → load → transform, with raw data kept immutable;
- handle API pagination, rate limits, retries with backoff, and schema drift;
- explain change data capture (CDC) conceptually and when it beats polling.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| *Fundamentals of Data Engineering* chapters 7 (Ingestion) and 8 (Transformation, first half) | Read fully. | 3 h |
| [dlt documentation](https://dlthub.com/docs) | *Getting started*, *Incremental loading*, *Write dispositions*, *Schema evolution*. | 2 h |
| Data Engineering Zoomcamp, week 2 (workflow orchestration) — the ingestion parts | Watch the ingestion videos only; orchestration is M7. | 1.5 h |
| [Debezium: CDC concepts](https://debezium.io/documentation/reference/stable/tutorial.html) | Read the tutorial introduction for the concept only; do not deploy it. | 0.5 h |

## Practice

1. Write, by hand (no framework), a Python extractor for the [Open-Meteo](https://open-meteo.com/) API for ten cities and 30 days of hourly data: pagination or date-chunking, retries with exponential backoff, raw responses landed as newline-delimited JSON with the request timestamp in the filename.
2. Load the raw files into Postgres with an idempotent strategy. Run the pipeline three times; prove the row count is stable. Then delete one day of raw data, re-run, and prove it is restored.
3. Make the extraction incremental using a watermark stored in a `pipeline_state` table. Simulate late-arriving data and decide how far back to re-extract.
4. Rebuild step 1–3 with `dlt` in far fewer lines. Compare: what did the framework do that I did by hand, and what did it hide?
5. Ingest the Olist database from Postgres to DuckDB (database-to-database) incrementally using `updated_at`-style cursors you add to the source tables.

## Build

**The pipeline, v1.** `projects/pipeline/` containing: a raw landing zone layout (`raw/<source>/<date>/…`),
extractors for the weather API and for the Olist Postgres database, idempotent loaders into a
`warehouse` Postgres database (or DuckDB file), a `pipeline_state` table, and a `README.md` that
states the idempotency guarantee and how to backfill a date range. Include a `make backfill START END` (or `uv run` equivalent) command.

## Check yourself

- Define idempotent. Give three loading strategies that achieve it and the cost of each.
- What is a watermark, and what goes wrong with `WHERE updated_at > :last_run` if clocks or transactions are slow?
- Why keep raw data immutable? What does that let me do when I find a transformation bug?
- When would I choose CDC over incremental polling?
- What should happen when the source adds a column? Removes one? Changes a type?
- Where does the transformation step belong in ELT, and why did the answer change over the last decade?

## Done when

- [ ] Hand-written extractor with retries and raw landing works.
- [ ] Idempotency demonstrated by repeat runs and by deleting and re-running.
- [ ] Incremental extraction with a state table and late-data handling.
- [ ] Same pipeline rebuilt with dlt, with a written comparison.
- [ ] `projects/pipeline/` v1 complete with a documented backfill command.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entries written.

## My notes

_Link to `notes/m06-ingestion-and-pipelines.md` once written._
