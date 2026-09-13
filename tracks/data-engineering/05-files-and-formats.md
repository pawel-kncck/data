---
title: "M5 · Python, files and formats"
parent: "Phase 2: Data engineering"
nav_order: 1
---

# M5 · Python, files and formats
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** Phase 1

1. TOC
{:toc}

## Why this matters

Most data engineering is moving bytes between formats. Knowing why Parquet is fast, why CSV is
a trap, and how compression and partitioning interact saves more time than any framework. This
module also settles the Python data toolkit used for the rest of the program.

## Learning outcomes

By the end I can:

- explain row vs columnar layouts, and what Parquet's row groups, column chunks, encodings and statistics enable;
- read and write CSV, JSON (including newline-delimited), Parquet and Arrow with Polars and DuckDB;
- choose compression (snappy, zstd, gzip) and explain the trade-off;
- partition files on disk by a column and explain when it helps (partition pruning) and when it hurts (small files);
- process a dataset larger than memory with streaming or lazy evaluation;
- explain schema evolution problems in each format.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| [Polars user guide](https://docs.pola.rs/) | *Concepts* and *Expressions* sections, plus *Lazy API* and *IO*. | 2.5 h |
| [Apache Parquet: file format](https://parquet.apache.org/docs/file-format/) | Read the layout, metadata and encoding pages. | 1 h |
| [DuckDB: Parquet and CSV import](https://duckdb.org/docs/data/overview) | Read the Parquet, CSV and partitioned-data pages. | 1 h |
| *Fundamentals of Data Engineering* chapter 6 (Storage) | Read; note the "storage abstractions" and file-format sections. | 1.5 h |

## Practice

1. Download three months of NYC yellow taxi trips (they ship as Parquet). Convert one month to CSV, gzipped CSV, newline-delimited JSON, Parquet-snappy and Parquet-zstd. Record file size and the time for `count(*)`, a filtered aggregate, and a `SELECT *` in DuckDB for each.
2. Write the three months as a Hive-partitioned dataset by `year/month`. Show with `EXPLAIN` in DuckDB that a filter on month prunes partitions. Then partition by `pickup_location_id` and observe the small-files problem.
3. With Polars lazy mode, compute daily revenue per pickup zone over all three months while keeping memory under a limit that fails in eager mode.
4. Break schema evolution: add a column in month two, change a type in month three, and read all three together in DuckDB and Polars. Document what each tool does.

## Build

**Format benchmark.** `projects/format-bench/` with the conversion and benchmark scripts and a
`REPORT.md` with the results table and a decision guide: which format, compression and
partitioning I would choose for (a) a raw landing zone, (b) an analytics dataset, (c) a data
exchange with a partner who uses Excel.

## Check yourself

- Why can a Parquet reader skip whole row groups for `WHERE pickup_date = '2024-01-05'`? What has to be true of the data for that to work?
- What does dictionary encoding do and when does it fail to help?
- What is the small-files problem and what is a reasonable target file size?
- Why is CSV type inference dangerous? Give two concrete failures.
- What does "lazy" buy in Polars beyond memory?

## Done when

- [ ] Benchmark table for five formats produced.
- [ ] Partition pruning demonstrated and the small-files problem observed.
- [ ] Larger-than-memory aggregation runs in lazy mode.
- [ ] Schema evolution behaviour documented for both tools.
- [ ] `projects/format-bench/REPORT.md` complete with the decision guide.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m05-files-and-formats.md` once written._
