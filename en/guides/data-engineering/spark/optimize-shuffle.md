---
title: Optimize Spark Shuffle — Guide
description: Execution guide: how to optimize Spark shuffle (technical seminar level)
published: true
tags: [guide, data-engineering, spark, performance]
---

# Optimize Spark Shuffle

Synthesizes concepts from apache-spark.md and sources (Netflix autoscaler, AWS lakehouse, Databricks engineering).

## Approach
1. Minimize shuffle: filter early, use broadcast joins for small tables
2. Tune `spark.sql.adaptive.enabled` (AQE) for skew handling
3. Monitor `spark.sql.shuffle.partitions` vs data size
4. Use `spark.locality.wait` for data locality

## When to apply
Large-scale ETL where network I/O dominates. Reference Netflix Flink autoscaler for comparison of scaling strategies.
