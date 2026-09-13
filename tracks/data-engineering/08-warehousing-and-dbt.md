---
title: "M8 · Warehousing and analytics engineering"
parent: "Phase 2: Data engineering"
nav_order: 4
---

# M8 · Warehousing and analytics engineering
{: .no_toc }

**Time budget:** 2 weeks (16 h) · **Prereqs:** M2, M7

1. TOC
{:toc}

## Why this matters

The warehouse is where engineering meets analytics. Dimensional modeling is a forty-year-old idea
that still decides whether analysts can answer questions in one join or ten. dbt is how those
models are built, tested and documented as code today. This module is the bridge between the two
halves of the program.

## Learning outcomes

By the end I can:

- explain facts, dimensions, grain, star vs snowflake schemas, and conformed dimensions;
- design a dimensional model from a business process by declaring the grain first;
- implement slowly changing dimensions (type 1 and type 2) and explain when each applies;
- structure a dbt project (sources, staging, intermediate, marts), with tests, documentation and incremental models;
- explain why OLAP engines differ from OLTP (columnar storage, vectorised execution, no indexes);
- contrast Kimball with One Big Table, Data Vault and the "medallion" layering, and say when each fits.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| *The Data Warehouse Toolkit*, chapters 1–4 | Read closely. Chapter 2's list of techniques is the checklist. | 4 h |
| [dbt Fundamentals course](https://learn.getdbt.com/) | Complete it (models, sources, tests, docs, deployment). | 4 h |
| [dbt docs: How we structure our dbt projects](https://docs.getdbt.com/best-practices/how-we-structure/1-guide) | Read the whole guide. | 1 h |
| [dbt docs: Incremental models](https://docs.getdbt.com/docs/build/incremental-models) and [Snapshots](https://docs.getdbt.com/docs/build/snapshots) | Read. | 1 h |
| *Fundamentals of Data Engineering* chapter 8 (Transformation, modeling section) | Read the modeling comparison. | 1 h |

## Practice

1. For Olist, write down the business processes (order placed, item shipped, payment made, review left). For each: the grain, the dimensions, the measures. Decide which becomes a fact table in v1.
2. Design the star schema: `fct_orders`, `fct_order_items`, `dim_customers`, `dim_products`, `dim_sellers`, `dim_date`. Write the grain statement at the top of each model file.
3. Build it in dbt on DuckDB (`dbt-duckdb`) or Postgres, from the raw tables the M6 pipeline loaded. Layers: `staging` (rename, cast, one model per source table) → `intermediate` → `marts`.
4. Add tests: `unique` and `not_null` on keys, `relationships` between facts and dims, `accepted_values` on status, and one custom test (for example, no order item without an order). Make one fail on purpose and fix the data or the model.
5. Turn `dim_customers` into a type 2 SCD with a dbt snapshot; change a customer's city in the source and show both versions.
6. Make `fct_order_items` incremental; re-run and show that only new rows are processed.
7. Generate and read the dbt docs site. Write descriptions for every mart column.

## Build

**The warehouse.** `projects/warehouse/` with the dbt project, an ER diagram of the marts, and a
README stating each fact table's grain. Wire `dbt build` into the Airflow DAG from M7 so the
whole path (extract → load → transform → test) runs on schedule. Answer the five M1 Olist
questions again using only the marts, and note how much simpler the SQL became.

## Check yourself

- What is grain and why must it be declared before choosing dimensions?
- Give an example where a snowflaked dimension is justified, and why a star is usually preferred.
- How does a type 2 SCD change the way a fact row joins to its dimension? What key does the fact store?
- What is a conformed dimension and what problem does it solve across marts?
- Why does dbt insist on `ref()` instead of hard-coded table names?
- When is an incremental model wrong, and how do I make it safe to full-refresh?
- What does One Big Table gain and lose relative to a star schema?

## Done when

- [ ] Grain, dimensions and measures written for each business process.
- [ ] dbt project builds clean: staging → intermediate → marts with all tests passing.
- [ ] Type 2 SCD snapshot working with a demonstrated change.
- [ ] Incremental fact model working.
- [ ] dbt docs generated with column descriptions on all marts.
- [ ] `dbt build` runs from Airflow after the loads.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entries written.

## My notes

_Link to `notes/m08-warehousing-and-dbt.md` once written._
