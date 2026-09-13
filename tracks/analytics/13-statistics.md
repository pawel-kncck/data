---
title: "M13 · Statistics for analysts"
parent: "Phase 3: Data analytics"
nav_order: 2
---

# M13 · Statistics for analysts
{: .no_toc }

**Time budget:** 2 weeks (16 h) · **Prereqs:** M12

1. TOC
{:toc}

## Why this matters

Statistics is the difference between "the number went up" and "the number went up, and here is
how sure I am, and here is what would change my mind". The goal is not to derive estimators; it
is to reason correctly about uncertainty, to know which test applies, to design an experiment that
can actually answer a question, and to spot the mistakes that make most published analyses wrong.

## Learning outcomes

By the end I can:

- describe a distribution with the right summary (mean vs median, spread, skew) and choose the right visual;
- explain sampling distributions, standard error and confidence intervals, and compute them by bootstrap;
- run and interpret a hypothesis test (two-proportion z-test, t-test, chi-square, Mann–Whitney) and explain p-values correctly;
- compute the sample size an A/B test needs, and explain power, minimum detectable effect and the peeking problem;
- design an A/B test end to end: hypothesis, unit of randomisation, metric, guardrails, duration, analysis plan;
- recognise the standard errors of practice: multiple comparisons, p-hacking, survivorship, regression to the mean, confounding vs causation;
- fit and interpret a simple linear and logistic regression as descriptive tools, and know their limits.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| *OpenIntro Statistics* chapters 1–2, 5–7 | Read; do a selection of end-of-chapter exercises. Skip 3–4 if probability is familiar. | 5 h |
| *Statistics Done Wrong* (free online) | Read the whole book. It is short. | 2 h |
| *Trustworthy Online Controlled Experiments* chapters 1–5 | Read. | 3 h |
| [Evan Miller: How Not To Run an A/B Test](https://www.evanmiller.org/how-not-to-run-an-ab-test.html) | Read; then use the sample-size calculator. | 0.5 h |
| [Seeing Theory](https://seeing-theory.brown.edu/) | Play with the CLT and confidence interval visualisations. | 0.5 h |

## Practice

1. Olist review scores: describe the distribution. Is the mean a good summary? Bootstrap a 95% confidence interval for the mean and for the share of 1-star reviews.
2. Is late delivery associated with lower review scores? Choose the right test, state hypotheses, run it, report the effect size with an interval, and then write two plausible confounders.
3. Simulate an A/B test on synthetic data with a true effect of 2% relative lift on a 5% conversion rate. Compute the required sample size for 80% power. Run 1,000 simulated experiments and check the false negative rate. Then simulate peeking (checking daily and stopping at first significance) and measure the inflated false positive rate.
4. Compare AOV between two seller groups with a t-test and with Mann–Whitney. Explain when the conclusions could differ.
5. Fit a regression of delivery time on distance, seller state and product weight. Interpret the coefficients. Then argue why none of them is a causal effect.
6. Take one published analysis (a blog post, a news chart) and find the statistical flaw. Write it up in one paragraph.

## Build

**Experiment design document.** `projects/analytics/experiment/`: a proposal for one experiment
Olist could run (for example, showing estimated delivery date on the product page), with
hypothesis, randomisation unit, primary and guardrail metrics, MDE, sample size and duration,
analysis plan with the exact test, and stopping rules. Plus a notebook with the simulation study
from practice 3 and a short "what I would say to someone who wants to stop the test early".

## Check yourself

- Explain a p-value in one sentence without saying "probability the hypothesis is true".
- What does a 95% confidence interval mean, and what does it not mean?
- Double the sample size: what happens to the standard error? To the minimum detectable effect?
- Why does peeking inflate false positives? Name a method that allows it.
- What is the unit of randomisation and why does randomising by session when the metric is per user cause trouble?
- Give three explanations, other than causation, for a strong correlation.
- When is the median a better summary than the mean? When is neither enough?

## Done when

- [ ] Bootstrap intervals computed and interpreted.
- [ ] Late-delivery vs review analysis done with the right test and confounders named.
- [ ] Simulation study done: power verified and peeking inflation measured.
- [ ] Regression fitted and interpreted with a causal caveat.
- [ ] One flawed analysis critiqued.
- [ ] `projects/analytics/experiment/` complete.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entries written.

## My notes

_Link to `notes/m13-statistics.md` once written._
