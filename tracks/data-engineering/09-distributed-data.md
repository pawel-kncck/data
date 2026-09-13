---
title: "M9 · Distributed data and the lakehouse"
parent: "Phase 2: Data engineering"
nav_order: 5
---

# M9 · Distributed data and the lakehouse
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** M5, M8

1. TOC
{:toc}

## Why this matters

Everything so far fits on one machine, and honestly most workloads do. But the vocabulary of
distributed systems (partitioning, replication, shuffles, consistency) is how warehouses,
lakehouses and streaming systems are explained, and knowing when a single DuckDB process beats
a cluster is itself a valuable skill. This module is deliberately conceptual with one hands-on
taste of Spark and one of a lakehouse table format.

## Learning outcomes

By the end I can:

- explain replication (leader-based, multi-leader, leaderless) and the failure modes of each;
- explain partitioning/sharding by key and by range, and what a hot partition is;
- explain the MapReduce and dataflow model, what a shuffle is, and why it dominates cost;
- run a PySpark job locally, read its plan, and explain narrow vs wide transformations;
- explain what a lakehouse table format (Iceberg, Delta) adds to a folder of Parquet files: ACID, schema evolution, time travel, hidden partitioning;
- decide between DuckDB, Postgres, Spark and a managed warehouse for a given workload and data size.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| *DDIA* chapters 5 (Replication) and 6 (Partitioning) | Read fully. | 3 h |
| *DDIA* chapter 10 (Batch Processing) | Read fully; the MapReduce-to-dataflow narrative matters. | 1.5 h |
| [PySpark: Quickstart, DataFrame](https://spark.apache.org/docs/latest/api/python/getting_started/quickstart_df.html) | Do it locally with `pip install pyspark`. | 1 h |
| [Apache Iceberg: Introduction and Spec overview](https://iceberg.apache.org/docs/latest/) | Read the introduction and the table spec overview (metadata, manifests, snapshots). | 1 h |
| Data Engineering Zoomcamp, week 5 (batch/Spark) | Watch selectively: internals, partitions, joins. | 1.5 h |

## Practice

1. With local PySpark, compute daily revenue per zone on three months of NYC taxi data. Look at the physical plan; identify the exchange (shuffle). Re-partition by date before the aggregation and compare stage counts and time.
2. Do the same computation in DuckDB on one machine. Record both times. Write one paragraph on where the crossover would be.
3. Join trips to the zone lookup table two ways: normal join and broadcast join. Compare the plans.
4. Create an Iceberg table (via PySpark or `pyiceberg` with a local catalog) from the taxi Parquet files. Append a month, update some rows, then query the previous snapshot (time travel). Look at the metadata files on disk and map them to the spec.
5. Read the replication section of the Postgres docs and set up a streaming replica in Compose. Kill the primary and observe what a client sees.

## Build

**Scale decision memo.** `projects/scale-memo/REPORT.md`: the benchmark results (DuckDB vs
Spark), the shuffle experiment, the Iceberg exercise with the snapshot metadata explained, and
a one-page decision guide "which engine for which job" with the reasoning I would give a team.

## Check yourself

- What can go wrong with asynchronous replication that cannot go wrong with synchronous? What does synchronous cost?
- Why does a range partition by timestamp create hot spots for writes?
- What is a shuffle, and which operations cause one?
- Why does a broadcast join avoid a shuffle, and when is it unsafe?
- What does Iceberg store that plain Parquet cannot, and how does it make a write atomic on object storage?
- A team wants Spark for 20 GB of daily data. What do I ask, and what do I probably recommend?

## Done when

- [ ] Spark job runs locally; plan read; repartition experiment recorded.
- [ ] DuckDB vs Spark benchmark recorded with a crossover paragraph.
- [ ] Iceberg table created with append, update and time travel demonstrated.
- [ ] Postgres replica set up and failover observed.
- [ ] `projects/scale-memo/REPORT.md` complete.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m09-distributed-data.md` once written._
