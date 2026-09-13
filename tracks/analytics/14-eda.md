---
title: "M14 · Exploratory data analysis"
parent: "Phase 3: Data analytics"
nav_order: 3
---

# M14 · Exploratory data analysis
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** M12, M13

1. TOC
{:toc}

## Why this matters

Exploratory data analysis is the analyst's core loop: look, question, look again. Done badly it is
an aimless notebook of forty histograms. Done well it is a disciplined search that ends with a
small number of findings that hold up. This module builds the discipline and the tooling reflexes
(SQL first, dataframes when needed, a chart for every question).

## Learning outcomes

By the end I can:

- run a repeatable EDA sequence: shape and grain → completeness → distributions → relationships → time → segments → anomalies;
- profile a dataset quickly (row counts, keys, nulls, cardinalities, outliers) with SQL and Polars;
- move fluidly between DuckDB SQL and Polars, and know when each is the better tool;
- keep a notebook readable: hypotheses stated before charts, findings summarised, dead ends noted;
- distinguish a finding (holds across segments and time) from an artefact (of the data collection, the join, or the chart);
- tidy messy data: reshape wide/long, fix types, deduplicate, handle missing values explicitly.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| [Tidy Data](https://vita.had.co.nz/papers/tidy-data.pdf) — Hadley Wickham | Read; it is short and changes how I structure tables. | 1 h |
| *Python Data Science Handbook* chapter 3 (pandas) | Skim for reference; know what is there. | 1 h |
| [Polars user guide: Transformations](https://docs.pola.rs/user-guide/transformations/) | Joins, concatenation, pivots, melts. | 1 h |
| [DuckDB: SUMMARIZE](https://duckdb.org/docs/guides/meta/summarize) and friendly SQL features | Read; use them in every profiling step. | 0.5 h |
| A worked EDA by an experienced analyst (a Kaggle notebook with high votes on Olist) | Read critically: what did they check first, and what did they miss? | 1.5 h |

## Practice

1. Profile every Olist table with `SUMMARIZE` and a Polars null/cardinality report. Confirm the grain of each and find the two tables where the assumed key is not unique.
2. Answer, with the EDA sequence above: "What drives late delivery?" State three hypotheses first. Test each. Record which survived.
3. Find at least two artefacts: something that looks like a finding but is caused by the data (a truncated period, a join fan-out, a default value). Document how each was detected.
4. Reshape the payments table from long to wide (one row per order, one column per payment type) and back. Do it in SQL and in Polars.
5. Time-box a 45-minute EDA on a dataset I have never seen (any Kaggle dataset). Write the three most important things learned and the three questions I would ask the owner.

## Build

**EDA notebook: late deliveries.** `projects/analytics/eda-late-delivery.ipynb` with a fixed
structure: question, data and grain, hypotheses, one section per hypothesis (query, chart,
verdict), artefacts found, findings that survived, what I would do next. Export to HTML for the
site. The findings feed directly into M15 and M16.

## Check yourself

- List the EDA sequence from memory and say what each step protects against.
- How do I detect a join fan-out after the fact? How do I prevent it before?
- When would I reach for Polars instead of SQL in DuckDB, and vice versa?
- What are the three rules of tidy data?
- Give three ways missing values arise and why each needs a different treatment.
- What is the difference between an outlier and an error?

## Done when

- [ ] All tables profiled with grain confirmed and the non-unique keys found.
- [ ] Late-delivery EDA done with hypotheses stated before analysis.
- [ ] Two artefacts documented.
- [ ] Reshape exercise done both ways.
- [ ] 45-minute cold EDA written up.
- [ ] Notebook exported to HTML and linked from this page.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m14-eda.md` once written._
