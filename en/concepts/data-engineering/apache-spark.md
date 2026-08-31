---
title: Apache Spark — Concept
description: Apache Spark core concept for SW engineers (technical seminar level)
published: true
tags: [concept, data-engineering, spark, distributed-computing]
---

# Apache Spark

## Overview {.tabset}

### What it is
Open-source unified analytics engine for large-scale data processing. Memory-based cluster computing with RDD / DataFrame / Dataset APIs.

### Key properties
- Fault-tolerant (RDD lineage)
- Multi-language (Scala, Java, Python, SQL)
- Batch + stream unification (Structured Streaming)
- Lazy evaluation + DAG optimization

### When to use
ETL at scale, stream processing (Kafka → Spark Streaming), ML pipelines (MLlib / Spark ML).

## Architecture
Driver → Cluster Manager → Workers (Executors). Tasks scheduled via DAG Scheduler.

## Related Sources
- en/sources/articles/netflix-techblog.md (Flink autoscaler comparison)
- en/sources/articles/aws-bigdata.md (lakehouse with Spark on EC2)
- en/sources/articles/databricks-engineering.md

## Related Guides
- guides/data-engineering/spark/optimize-shuffle.md
- guides/data-engineering/spark/optimize-join.md
