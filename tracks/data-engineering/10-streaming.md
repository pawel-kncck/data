---
title: "M10 · Streaming basics"
parent: "Phase 2: Data engineering"
nav_order: 6
---

# M10 · Streaming basics
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** M4, M6, M9

1. TOC
{:toc}

## Why this matters

Streaming is where the ideas from M4 (ordering, exactly-once, idempotency) and M9 (partitions,
replication) come together. Most teams need less streaming than they think, but the log
abstraction underneath Kafka is one of the most useful ideas in data infrastructure, and event
time vs processing time trips up every analyst who has ever counted "yesterday's" events.

## Learning outcomes

By the end I can:

- explain the log abstraction: topics, partitions, offsets, consumer groups, retention;
- explain delivery guarantees (at-most-once, at-least-once, effectively-once) and how idempotent consumers achieve the last;
- explain event time vs processing time, watermarks and windows (tumbling, sliding, session);
- run a local Kafka-compatible broker (Redpanda), write a producer and a consumer in Python, and handle rebalances;
- stream events into the warehouse in micro-batches and reconcile with a batch load;
- explain when streaming is warranted and when a five-minute batch is the better answer.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| *DDIA* chapter 11 (Stream Processing) | Read fully. | 2 h |
| [Kafka documentation: Introduction and Design](https://kafka.apache.org/documentation/#gettingStarted) | Read *Introduction* and *Design* (4.1–4.8). | 2 h |
| [Redpanda quickstart](https://docs.redpanda.com/current/get-started/quick-start/) | Follow the Docker quickstart. | 0.5 h |
| Data Engineering Zoomcamp, week 6 (streaming) | Watch the concept videos. | 1.5 h |

## Practice

1. Start Redpanda via Compose. Write a producer that replays one hour of [GH Archive](https://www.gharchive.org/) events into a topic keyed by repository, at 100× speed with the original timestamps as event time.
2. Write a consumer that counts events per repository per five-minute **event-time** window, and prints the counts as windows close. Then delay a subset of events and observe late data. Decide on an allowed lateness and implement it.
3. Kill and restart the consumer mid-stream. Show duplicates with auto-commit, then make the consumer idempotent (dedupe by event id in the sink) and show the counts are correct.
4. Run two consumers in one group and watch partition assignment and rebalancing.
5. Sink the events into the M8 warehouse's raw layer in micro-batches and compare totals against a batch load of the same hour from the archive files.

## Build

**The pipeline, v3: a streaming source.** Add `projects/pipeline/streaming/` with the Compose
service, producer, consumer with event-time windows and idempotent sink, and a README that
states the delivery guarantee achieved and how it was verified. Add a section to the pipeline
README: "when I would use this instead of the batch path".

## Check yourself

- What does a consumer group guarantee about partition ownership? What happens to ordering across partitions?
- Explain how at-least-once delivery plus an idempotent sink gives effectively-once results.
- An event with timestamp 09:59 arrives at 10:03. Which windows does it belong to in event time and in processing time? What is a watermark for?
- Why does a keyed topic preserve per-key ordering, and what does that imply about choosing the key?
- What would make me choose streaming over hourly batch for a given use case? Name two costs of streaming.

## Done when

- [ ] Producer and windowed consumer work on GH Archive data.
- [ ] Late data handled with an explicit allowed lateness.
- [ ] Duplicates demonstrated and eliminated with an idempotent sink.
- [ ] Rebalancing observed.
- [ ] Streaming sink reconciled against batch.
- [ ] `projects/pipeline/streaming/` documented.
- [ ] *Check yourself* answered from memory with at most one miss.
- [ ] Log entry written.

## My notes

_Link to `notes/m10-streaming.md` once written._
