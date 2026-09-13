---
title: "M15 · Visualization and dashboards"
parent: "Phase 3: Data analytics"
nav_order: 4
---

# M15 · Visualization and dashboards
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** M14

1. TOC
{:toc}

## Why this matters

A chart is an argument. Most charts argue nothing because they show everything. This module is
about choosing the chart that makes one point, removing what does not serve it, and then the
different discipline of building a dashboard that people will actually use to monitor something
rather than to be impressed once.

## Learning outcomes

By the end I can:

- choose a chart type from the question (comparison, distribution, relationship, change over time, part-to-whole) and explain why the alternatives are worse;
- apply the basics of visual encoding: position beats length beats colour; declutter; direct labels; a title that states the finding;
- build clean charts in Plotly (interactive) and Matplotlib (static) with a reusable style;
- design a dashboard with a clear purpose, a hierarchy (headline metrics → trends → breakdowns), and definitions visible;
- build and publish a dashboard on the M8 warehouse with Evidence (code-first) or Metabase (GUI);
- critique a chart or dashboard specifically and constructively.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| *Storytelling with Data* chapters 1–6 | Read; redo one "before/after" from the book myself. | 3 h |
| [From Data to Viz](https://www.data-to-viz.com/) | Walk the decision tree for five questions; read the "caveats" pages. | 1 h |
| [Plotly Express docs](https://plotly.com/python/plotly-express/) | Skim; learn the `template` and `update_layout` idioms. | 1 h |
| [Evidence docs](https://docs.evidence.dev/) or [Metabase docs](https://www.metabase.com/docs/) | Getting started; connect to the warehouse. | 1 h |
| [Financial Times Visual Vocabulary](https://github.com/Financial-Times/chart-doctor/tree/main/visual-vocabulary) | Keep the poster open while choosing charts. | 0.5 h |

## Practice

1. Take five findings from the M14 notebook. For each, draw (on paper first) the chart that makes the point, then build it. Title each with the finding, not the variable names.
2. Take one default-styled chart and declutter it step by step, saving each step, until nothing can be removed.
3. Make the same comparison as a pie chart, a stacked bar, a grouped bar and a dot plot. Explain which reads fastest and why.
4. Build a reusable Plotly template (colours, fonts, gridlines, margins) and apply it to all charts.
5. Sketch the Olist operations dashboard on paper: purpose, audience, the one question it answers first, and the layout. Then build it.

## Build

**Olist operations dashboard.** `projects/analytics/dashboard/` on the M8 warehouse: headline
metrics (delivered order value, late-delivery rate, review score) with period comparison, trends,
breakdowns by state and seller, and a definitions panel linking to `METRICS.md` from M12.
Publish it (Evidence builds a static site; Metabase runs in Compose) and put screenshots on this
page. Include a `CRITIQUE.md` with a self-review against the principles from *Storytelling with Data*.

## Check yourself

- For each of comparison, distribution, relationship, change over time and part-to-whole: name the default chart and one trap.
- Why is a dual-axis chart usually a bad idea? What do I do instead?
- What is the difference between a dashboard and a report, and what does each need that the other does not?
- Name five things to remove from a default chart.
- When is a table better than a chart?
- Colour: how many categories can it distinguish before it stops working, and what do I do for more?

## Done when

- [ ] Five finding-titled charts built from the M14 notebook.
- [ ] Declutter sequence saved.
- [ ] Chart-type comparison written up.
- [ ] Plotly template in use.
- [ ] Dashboard published with screenshots and `CRITIQUE.md`.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m15-visualization.md` once written._
