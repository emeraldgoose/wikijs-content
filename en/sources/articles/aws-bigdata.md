---
title: AWS Big Data — Lakehouse Source
description: AWS lakehouse architecture (Iceberg, Spark, Redshift) source summary for seminar.
published: true
tags: [source, rss, aws, data-engineering, lakehouse, spark, iceberg]
---

# AWS Big Data Blog — Lakehouse Source

Feed: https://aws.amazon.com/blogs/big-data/feed/ (tier 1)

## Key Article (read full body)

Title: Razor Group's journey to a modern data lakehouse on AWS (Aug 28, 2026)

Summary (technical writer / seminar level):
- Migration from always-on Redshift clusters to open lakehouse (Apache Iceberg on S3 Tables, Spark, Redshift for BI)
- Architecture: Bronze/Silver/Gold Iceberg tables; AWS Glue Catalog + Lake Formation governance; Spark Connect on EC2 for ETL; serverless Redshift for ad-hoc
- Results: 65% faster P95 queries, 63% infrastructure cost reduction, workload isolation via elastic per-engine scaling

Full-body observations:
- Lakehouse combines data lake economics with warehouse governance (ACID, time travel, schema evolution via Iceberg)
- Multi-engine flexibility: Spark for heavy ETL, serverless queries for exploration, Redshift for BI dashboards
- Key insight: single open-format data lake prevents duplication; compute scales independently

Related Concepts: data-engineering/apache-spark.md, infrastructure/kubernetes.md (for EKS workload context), data-engineering/delta-lake.md (compare Iceberg vs Delta)
