---
title: "M3 · Storage, indexes and query plans"
parent: "Phase 1: Databases"
nav_order: 3
---

# M3 · Storage, indexes and query plans
{: .no_toc }

**Time budget:** 2 weeks (16 h) · **Prereqs:** M2

1. TOC
{:toc}

## Why this matters

"Add an index" is the most common performance advice and the most commonly wrong. Knowing how
rows sit in pages, how a B-tree is walked, and how the planner estimates cost turns performance
work from guessing into reading. The same ideas (row vs column layout, sorted runs, LSM trees)
explain why DuckDB, Parquet and every warehouse behave the way they do.

## Learning outcomes

By the end I can:

- describe how a heap table is laid out in pages and what a tuple header contains;
- explain B+tree indexes, when they help, when they hurt, and what a covering index is;
- read `EXPLAIN (ANALYZE, BUFFERS)` output: scan types, join algorithms, row estimates vs actuals, buffer hits;
- recognise the common causes of bad plans (stale statistics, functions on indexed columns, implicit casts, low selectivity);
- contrast row stores with column stores and LSM trees with B-trees, with the workloads each suits;
- explain what `VACUUM` and `ANALYZE` do and why MVCC makes them necessary.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| CMU 15-445, lectures 3–8 (Storage, Buffer Pools, Hash Tables, Trees, Index Concurrency) | Watch at 1.5×; notes on pages, slotted layout, B+tree operations. Skip index concurrency if short on time. | 5 h |
| *DDIA* chapter 3 (Storage and Retrieval) | Read fully. This is the chapter I will reread most. | 2 h |
| [Use The Index, Luke!](https://use-the-index-luke.com/) | Chapters 1–4 (Anatomy of an Index, Where Clause, Performance and Scalability, Join). | 3 h |
| [PostgreSQL manual: Using EXPLAIN](https://www.postgresql.org/docs/current/using-explain.html) | Read fully. | 1 h |
| [PostgreSQL manual: Indexes](https://www.postgresql.org/docs/current/indexes.html) | Read 11.1–11.9 (types, multicolumn, ordering, combining, unique, expression, partial). | 1.5 h |
| *Database Internals* part I (optional) | Chapters 2–4 if the CMU material felt too fast. | — |

## Practice

1. On the Olist database from M2, scale a table up (generate 10 million synthetic order items with `generate_series`). Then, for ten queries of my choosing, record the plan and timing **before** any index, hypothesise which index would help and why, add it, and record the plan **after**. Keep the ones that helped; write down the ones that did not and why.
2. Reproduce each of these and explain the plan: a sequential scan chosen despite an index (low selectivity); an index ignored because of `LOWER(email)`; an index ignored because of a type mismatch; a bad estimate fixed by `ANALYZE`; a nested loop vs hash join switch when the row count changes.
3. Compare the same aggregate query on the same data in Postgres and DuckDB. Explain the difference in time using row vs column storage.
4. Check `pg_stat_user_tables` for dead tuples after a large `UPDATE`; run `VACUUM` and observe.

## Build

**Index lab report.** A `projects/index-lab/` folder with the scripts that generate the data and
run the experiments, and a `REPORT.md` with the before/after plans for every experiment, a table of
timings, and a one-paragraph rule of thumb for each phenomenon I saw. This is the artefact I will
point to when someone says "just add an index".

## Check yourself

- Walk through a lookup of one key in a B+tree with a fanout of 500 over 100 million rows. How many page reads?
- Why can a partial index be dramatically smaller? Give a query it would serve.
- In an `EXPLAIN ANALYZE`, what does it mean when estimated rows are 10 and actual rows are 1,000,000? What do I do?
- Why does `WHERE created_at::date = '2024-01-01'` not use an index on `created_at`? How do I rewrite it?
- What does a column store make cheap, and what does it make expensive?
- What is write amplification in an LSM tree, and what is the corresponding cost in a B-tree?

## Done when

- [ ] Ten before/after index experiments documented.
- [ ] All five "bad plan" cases reproduced and explained.
- [ ] Postgres vs DuckDB comparison written up.
- [ ] `projects/index-lab/REPORT.md` complete.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entries written.

## My notes

_Link to `notes/m03-storage-and-indexes.md` once written._
