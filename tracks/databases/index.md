---
title: "Phase 1: Databases"
nav_order: 4
has_children: true
---

# Phase 1 · Databases
{: .no_toc }

**Time budget:** 7 weeks · **Prereqs:** [Phase 0](../00-setup.md)

The foundation for everything else. Four modules move from *using* a relational database to
*understanding* one: fluent SQL, a well-designed schema, what happens on disk when a query runs,
and what the database promises when many things happen at once.

| Module | Weeks | Outcome |
| --- | --- | --- |
| [M1 · SQL fundamentals](01-sql-fundamentals.md) | 2 | Joins, aggregation, CTEs and window functions without looking things up |
| [M2 · Data modeling and schema design](02-data-modeling.md) | 2 | Design and implement a normalised schema with the right constraints |
| [M3 · Storage, indexes and query plans](03-storage-and-indexes.md) | 2 | Read `EXPLAIN ANALYZE` and choose indexes on evidence |
| [M4 · Transactions and concurrency](04-transactions.md) | 1 | Explain isolation levels with anomalies reproduced by hand |

**Stack:** PostgreSQL 16 in Docker, DuckDB, `psql`, Python for scripting.

**Backbone reading:** CMU 15-445 lectures and *Designing Data-Intensive Applications* chapters 2, 3 and 7.
