---
title: "M2 · Data modeling and schema design"
parent: "Phase 1: Databases"
nav_order: 2
---

# M2 · Data modeling and schema design
{: .no_toc }

**Time budget:** 2 weeks (16 h) · **Prereqs:** M1

1. TOC
{:toc}

## Why this matters

A schema is the contract between everyone who touches the data. A bad one is the source of
most "data quality" problems downstream: duplicated facts, orphaned rows, columns that mean two
things. Learning to model well now pays off in M8 (dimensional modeling is a *different* set of
trade-offs made deliberately) and in every analysis that depends on trusting the source.

## Learning outcomes

By the end I can:

- turn a written description of a domain into an entity–relationship model with cardinalities;
- explain functional dependencies and normalise to 3NF/BCNF, and say when I would deliberately denormalise;
- choose keys (natural vs surrogate, composite, UUID vs sequence) and justify the choice;
- express business rules as constraints (`NOT NULL`, `UNIQUE`, `CHECK`, foreign keys with the right `ON DELETE` action);
- choose appropriate PostgreSQL types (`numeric` vs `float`, `timestamptz`, `text`, enums, `jsonb`) and know the traps;
- evolve a schema with migrations without losing data.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| CMU 15-445, lectures 1–2 (Relational Model, Modern SQL) | Watch; take notes on relational algebra. | 2.5 h |
| [PostgreSQL manual: Data Definition](https://www.postgresql.org/docs/current/ddl.html) | Read 5.1–5.5 (types, defaults, constraints, system columns) and 5.10 (inheritance) skim. | 2 h |
| [PostgreSQL manual: Data Types](https://www.postgresql.org/docs/current/datatype.html) | Read numeric, character, date/time, JSON sections. | 1 h |
| [Wikipedia: Database normalization](https://en.wikipedia.org/wiki/Database_normalization) | Work through the examples for 1NF–BCNF; write my own for each. | 1.5 h |
| *DDIA* chapter 2 (Data Models and Query Languages) | Read; note the relational vs document trade-offs. | 1.5 h |

## Practice

1. Take three domains (a library, a ride-sharing app, a course-enrolment system) and, for each: list entities and relationships, draw an ER diagram (Mermaid in a markdown file is fine), state the cardinalities, and identify the functional dependencies.
2. Take a deliberately bad flat table (one wide `orders.csv` with customer, product and seller columns repeated) and normalise it step by step, writing the schema at each normal form and the anomaly that each step removes.
3. Write the DDL for the ride-sharing app in Postgres with all constraints. Then write five `INSERT`s that *should* fail and confirm they do.
4. Convert the Olist CSVs into a properly constrained Postgres schema (foreign keys, `CHECK`s on statuses, `timestamptz`). Record every row that violates a constraint and decide what to do with it.

## Build

**Olist in Postgres.** A `projects/olist-db/` folder with: `schema.sql` (the normalised schema),
`load.py` (loads the CSVs with Polars and `COPY`, logging rejected rows), a Mermaid ER diagram
in the README, and a `migrations/` folder with at least one migration that changes the schema
after data is loaded (for example splitting a column) without losing data. This database is
reused in M3, M4 and M8.

## Check yourself

- What is a functional dependency? Give an example of a 2NF violation and a 3NF violation.
- Why is `float` wrong for money? Why is `timestamp` (without time zone) usually wrong?
- When would I choose a surrogate key over a natural key? What does a UUID primary key cost in a B-tree?
- What does `ON DELETE RESTRICT` vs `CASCADE` vs `SET NULL` do, and which is the safe default?
- Give a case where I would denormalise on purpose, and what I would do to keep the copy correct.
- How do I add a `NOT NULL` column to a large, live table without a long lock?

## Done when

- [ ] Three ER diagrams with cardinalities and dependencies written down.
- [ ] Normalisation exercise done with the anomaly named at each step.
- [ ] `projects/olist-db/` loads cleanly with constraints and has one working migration.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entries written.

## My notes

_Link to `notes/m02-data-modeling.md` once written._
