---
title: "M16 · Communicating analysis"
parent: "Phase 3: Data analytics"
nav_order: 5
---

# M16 · Communicating analysis
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** M14, M15

1. TOC
{:toc}

## Why this matters

An analysis that does not change a decision was entertainment. The last analytics module is about
the delivery: a short, structured memo with a recommendation, the evidence for it, the uncertainty
around it, and what would change the conclusion. It also covers the workflow around analysis
(scoping, reproducibility, review) that makes the next one faster.

## Learning outcomes

By the end I can:

- write a one-page analysis memo: recommendation first, then evidence, then caveats, then appendix;
- scope an analysis request with a stakeholder: the decision, the deadline, the options on the table, what "good enough" means;
- state uncertainty honestly without burying the recommendation;
- make an analysis reproducible: pinned environment, data snapshot or query with a date, notebook that runs top to bottom;
- run a self-review and a peer-style review checklist before sharing;
- present the memo in five minutes and handle the "but what about…" questions.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| *Storytelling with Data* chapters 7–9 (narrative) | Read. | 1.5 h |
| [Minto's Pyramid Principle, any concise summary](https://en.wikipedia.org/wiki/Barbara_Minto) | Learn the SCQA structure and answer-first ordering. | 0.5 h |
| Two real analysis write-ups from public data teams (for example, from company engineering blogs, or the *Airbnb* / *Spotify* research posts) | Read critically with the memo template next to them: what is missing? | 1.5 h |
| [Google: How to write a design doc](https://www.industrialempathy.com/posts/design-docs-at-google/) | Read for structure; adapt to analysis. | 0.5 h |

## Practice

1. Write the late-delivery memo from the M14 findings and M15 charts. One page. Recommendation in the first sentence.
2. Write the same memo for two audiences: the head of operations and an engineer who will implement the change. Note what changed.
3. Draft the scoping conversation for a new request ("why is review score dropping?") as a script: the questions I ask and the answers that would change what I do.
4. Make the M14 notebook fully reproducible: `uv` lockfile, a query with a fixed date range against a snapshot, a `make report` that rebuilds the HTML. Delete the environment and rebuild from scratch.
5. Record myself presenting the memo in five minutes. Watch it. Write down three things to fix, then re-record.

## Build

**Analysis memo and template.** `projects/analytics/memo/`: the final late-delivery memo
(Markdown, one page), `MEMO_TEMPLATE.md` for future analyses, `SCOPING_CHECKLIST.md`,
`REVIEW_CHECKLIST.md`, and the reproducible notebook build. Link the memo from the site.

## Check yourself

- What are the sections of a one-page analysis memo, in order, and why is the recommendation first?
- What questions must I answer before starting an analysis?
- Give two ways to state uncertainty that do not undermine the recommendation.
- What makes an analysis reproducible? Name the three most common things that break it.
- A stakeholder says "the number looks wrong". What do I do first?

## Done when

- [ ] One-page memo written and reviewed against the checklist.
- [ ] Two-audience rewrite done with notes.
- [ ] Scoping script written.
- [ ] Notebook rebuilds from scratch with one command.
- [ ] Presentation recorded twice.
- [ ] `projects/analytics/memo/` complete and linked.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m16-communication.md` once written._
