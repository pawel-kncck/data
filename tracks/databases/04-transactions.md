---
title: "M4 · Transactions and concurrency"
parent: "Phase 1: Databases"
nav_order: 4
---

# M4 · Transactions and concurrency
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** M3

1. TOC
{:toc}

## Why this matters

Every pipeline and every application relies on what the database promises when two things happen
at once, and most engineers have only a vague idea what those promises are. Reproducing the
anomalies by hand makes them concrete. This module also introduces the vocabulary (consistency
models, idempotency) that M6 and M10 build on.

## Learning outcomes

By the end I can:

- define atomicity, consistency, isolation and durability precisely, and say what each costs;
- describe the anomalies (dirty read, non-repeatable read, phantom, lost update, write skew) and which isolation level prevents each;
- explain how MVCC works in Postgres (snapshots, xmin/xmax, why readers do not block writers);
- explain locking (row locks, `SELECT ... FOR UPDATE`, advisory locks), deadlocks and how Postgres resolves them;
- choose an isolation level and a locking strategy for a given use case and justify it;
- explain what the write-ahead log is for and how it enables crash recovery and replication.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| *DDIA* chapter 7 (Transactions) | Read fully. The clearest treatment of anomalies anywhere. | 2 h |
| [PostgreSQL manual: Concurrency Control](https://www.postgresql.org/docs/current/mvcc.html) | Read chapter 13 fully. | 1.5 h |
| CMU 15-445, lectures on Concurrency Control Theory, 2PL and MVCC | Watch; focus on the intuition, not the proofs. | 2.5 h |
| [Jepsen: Consistency Models](https://jepsen.io/consistency) | Study the diagram; be able to place Postgres's levels on it. | 0.5 h |

## Practice

1. Open two `psql` sessions against the Olist database. At `READ COMMITTED`, reproduce a non-repeatable read and a lost update. At `REPEATABLE READ`, show the first disappears and the second raises a serialization error. At `SERIALIZABLE`, reproduce write skew being *prevented*.
2. Run the relevant tests from [Hermitage](https://github.com/ept/hermitage) for Postgres and check each result against the docs.
3. Create a deadlock deliberately, observe the error and the log message, then fix it by ordering lock acquisition.
4. Write a Python script that runs 50 concurrent "transfer money between accounts" transactions with and without `SELECT ... FOR UPDATE`. Show the balance totals are wrong without it.

## Build

**Anomaly playbook.** A `projects/transactions-lab/` folder with a script per anomaly (two-session
transcripts that reproduce it), the concurrent transfer script, and a `PLAYBOOK.md` table: anomaly
→ example → isolation level that prevents it → what it costs. Include my recommendation for
default isolation level in an application and in a batch pipeline, with reasons.

## Check yourself

- Explain write skew with the on-call doctors example. Why does `REPEATABLE READ` not prevent it?
- How does a reader in Postgres decide whether a tuple version is visible to it?
- Why does a long-running transaction cause table bloat?
- What is the difference between a serialization failure and a deadlock? How should an application handle each?
- What does `fsync` on the WAL guarantee, and what happens on a crash before and after it?
- What makes an operation idempotent, and why does that matter for retries?

## Done when

- [ ] All anomalies reproduced or shown prevented at the expected isolation levels.
- [ ] Deadlock reproduced and fixed.
- [ ] Concurrent transfer script demonstrates the lost update and its fix.
- [ ] `projects/transactions-lab/PLAYBOOK.md` complete.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m04-transactions.md` once written._
