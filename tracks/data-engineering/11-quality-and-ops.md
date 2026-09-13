---
title: "M11 · Data quality and operations"
parent: "Phase 2: Data engineering"
nav_order: 7
---

# M11 · Data quality and operations
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** M7, M8

1. TOC
{:toc}

## Why this matters

A pipeline that runs is not a pipeline that is right. This module adds the parts that make a
data platform trustworthy and maintainable: tests at the boundaries, contracts with sources,
monitoring that catches silent failures, and the boring operational hygiene (runbooks, cost,
access) that separates a project from a system.

## Learning outcomes

By the end I can:

- distinguish the dimensions of data quality (completeness, freshness, accuracy, consistency, uniqueness) and test for each;
- place tests at the right layer: source contracts, staging assertions, mart tests, and freshness checks;
- add anomaly-style monitoring (row counts, null rates, distributions over time) and alert on deviations;
- explain lineage and generate it from dbt;
- write a runbook for a pipeline failure and a rollback procedure for a bad load;
- reason about cost and performance of a warehouse workload, and about access control and PII handling.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| *Fundamentals of Data Engineering* chapter 2 (undercurrents: security, data management, DataOps) and chapter 9 (Serving) | Read. | 2 h |
| [dbt docs: Tests](https://docs.getdbt.com/docs/build/data-tests), [Source freshness](https://docs.getdbt.com/docs/build/sources#source-data-freshness), [Model contracts](https://docs.getdbt.com/docs/collaborate/govern/model-contracts) | Read. | 1.5 h |
| [Great Expectations: core concepts](https://docs.greatexpectations.io/docs/core/introduction/) | Read the concepts and one tutorial; decide whether it adds anything over dbt tests for this project. | 1.5 h |
| [Google SRE Book: chapter on postmortems](https://sre.google/sre-book/postmortem-culture/) | Read. It applies to data incidents directly. | 0.5 h |

## Practice

1. Add source freshness checks to every dbt source with realistic `warn_after` / `error_after` thresholds. Break one and watch the DAG fail loudly.
2. Add a model contract to `fct_orders` (enforced column types and constraints). Change a staging type and watch it fail at build time.
3. Build a `monitoring` schema: a daily job that records row counts, null rates and the distribution of key measures for each mart, and a query that flags any metric more than 3 standard deviations from its 30-day mean.
4. Inject three silent failures (a source stops updating; a currency column changes scale by 100; duplicate rows appear) and verify each is caught by a test, a contract or the monitor. Fix the ones that are not caught.
5. Write an incident postmortem for one of the injected failures, using the SRE template.
6. Identify PII in Olist (there is little, but customer zip prefix and unique id count). Decide on a policy: mask, hash or restrict, and implement it in staging.

## Build

**The pipeline, v4: operated.** Add to `projects/pipeline/`: `RUNBOOK.md` (how to detect,
diagnose, fix and roll back each failure class), the monitoring models, freshness and contract
configuration, one postmortem, and a `DATA_POLICY.md` for PII. Generate the dbt lineage graph and
include it in the README.

## Check yourself

- Name five data quality dimensions and one test for each.
- What is the difference between a test that runs after a build and a contract that blocks it? When do I want each?
- Why are row-count anomalies more useful than "is the table non-empty"?
- What should a runbook contain that a README does not?
- Describe how to roll back a bad daily load in the M6 pipeline design. What made it possible?
- What does "blameless" mean in a postmortem and why does it matter for data incidents?

## Done when

- [ ] Freshness checks and at least one model contract in place and exercised.
- [ ] Monitoring schema populated with an anomaly query.
- [ ] Three injected failures caught (after fixes).
- [ ] One postmortem written.
- [ ] `RUNBOOK.md` and `DATA_POLICY.md` complete; lineage graph in README.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m11-quality-and-ops.md` once written._
