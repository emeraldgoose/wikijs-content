---
title: Apache Spark — Concept (Seminar Level)
description: Seminar-level concept: Spark architecture, RDD/DAG, Structured Streaming, use cases.
published: true
tags: [concept, data-engineering, spark, distributed-computing]
---

# Apache Spark — Seminar Summary

Read from full documentation + source articles (AWS lakehouse, Netflix Flink comparison, Databricks engineering).

What: Unified batch + stream processing engine (memory-based cluster computing).
How: Driver submits DAG → Cluster Manager schedules → Workers run tasks; fault tolerance via RDD lineage.
Key APIs: RDD (low-level), DataFrame (structured), Dataset (typed).
Streaming: Structured Streaming treats stream as unbounded table; exactly-once semantics.
Performance: lazy evaluation + DAG optimization + Catalyst optimizer + Tungsten engine.
Use at Netflix / AWS: ETL backbone in lakehouse (Spark on EC2); comparison with Flink autoscaler for resource scaling.
