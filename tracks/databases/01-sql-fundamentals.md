---
title: "M1 · SQL fundamentals"
parent: "Phase 1: Databases"
nav_order: 1
---

# M1 · SQL fundamentals
{: .no_toc }

**Time budget:** 2 weeks (16 h) · **Prereqs:** [Phase 0](../00-setup.md)

1. TOC
{:toc}

## Why this matters

SQL is the one language every part of this program uses: the analyst writes it, the engineer
generates it, the database executes it. Fluency, not familiarity, is the goal. Fluency means I
can write a windowed cohort query without a search engine and know roughly what it will cost.

## Learning outcomes

By the end I can:

- explain the logical order of evaluation of a `SELECT` statement and use it to debug queries;
- write inner, left, self and anti joins and predict row counts before running them;
- use `GROUP BY`, `HAVING`, conditional aggregation and `DISTINCT ON` correctly;
- structure multi-step logic with CTEs and subqueries, and know when each is clearer;
- use window functions (`ROW_NUMBER`, `LAG`, `SUM() OVER`, frames) for running totals, rankings and sessionisation;
- handle `NULL` semantics, dates and intervals, and string operations without surprises;
- read a query someone else wrote and explain what it returns.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| [SQLBolt](https://sqlbolt.com/) | All lessons. Fast; skip what is obvious. | 2 h |
| [Select Star SQL](https://selectstarsql.com/) | All four chapters, including the exercises. | 2 h |
| [Mode SQL Tutorial](https://mode.com/sql-tutorial/) | *Intermediate* and *Advanced* sections, especially window functions. | 3 h |
| [PostgreSQL manual: Window Functions](https://www.postgresql.org/docs/current/tutorial-window.html) | Read carefully; understand frames (`ROWS` vs `RANGE`). | 1 h |
| [Modern SQL](https://modern-sql.com/) | Skim `FILTER`, `WITH`, `LATERAL`, `GROUPING SETS`. | 1 h |

## Practice

1. [pgexercises](https://pgexercises.com/): every category, in order. Load the dataset into local Postgres and solve there rather than in the browser. (~4 h)
2. [SQL Murder Mystery](https://mystery.knightlab.com/): solve it, then write the whole solution as a single query with CTEs. (~1 h)
3. Load the [Olist dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) into DuckDB and answer, without notes:
   - monthly revenue and its month-over-month change;
   - each customer's first and most recent order and days between them;
   - top three products per category by revenue (window function);
   - sellers with no orders in the last 90 days of the data (anti join);
   - the share of orders delivered late, by state, only for states with 100+ orders.

## Build

**SQL cookbook.** A `projects/sql-cookbook/` folder with one `.sql` file per pattern I found
non-obvious (gaps and islands, sessionisation, running totals with resets, pivots with conditional
aggregation, deduplication with `ROW_NUMBER`, top-N per group). Each file has the problem stated in a
comment, the query, and the expected result on a tiny inline dataset (`VALUES` clause) so it runs
anywhere.

## Check yourself

- In what order are `FROM`, `WHERE`, `GROUP BY`, `HAVING`, `SELECT`, `WINDOW`, `ORDER BY`, `LIMIT` evaluated? Why can't I use a `SELECT` alias in `WHERE`?
- What does `LEFT JOIN ... WHERE right.id IS NULL` compute? Give a second way to write it.
- What is the difference between `ROWS BETWEEN 1 PRECEDING AND CURRENT ROW` and `RANGE BETWEEN ...`?
- Why does `COUNT(column)` differ from `COUNT(*)`? What does `NULL = NULL` evaluate to?
- Write, from memory, a query that assigns a session id to events where a new session starts after 30 minutes of inactivity.
- When would a correlated subquery be slower than a join, and when would it not matter?

## Done when

- [ ] pgexercises completed, all categories.
- [ ] The five Olist questions answered, with queries saved in `projects/sql-cookbook/olist/`.
- [ ] Cookbook has at least six patterns with runnable examples.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entries written for both weeks.

## My notes

_Link to `notes/m01-sql-fundamentals.md` once written._
