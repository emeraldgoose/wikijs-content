---
title: AWS Big Data — Source (Full Body)
description: AWS Big Data Blog RSS feed — full-body summaries for seminar preparation
published: true
tags: [source, rss, aws, data-engineering, lakehouse, iceberg, spark, redshift]
locale: en
---

# AWS Big Data Blog

Feed: https://aws.amazon.com/blogs/big-data/feed/ (tier 1)

## Articles Read (Full Body)

### Razor Group's Journey to a Modern Data Lakehouse on AWS (Aug 28, 2026)
**Authors**: Yaswanth Kothainti, et al.

**Migration**: Always-on Redshift clusters → Open lakehouse (Apache Iceberg on S3 Tables, Spark, Redshift Serverless)

**Architecture**:
- **Storage**: Amazon S3 Tables with Iceberg (ACID, time travel, schema evolution, partition evolution) — single copy, multi-engine
- **Governance**: AWS Glue Data Catalog (unified metadata) + AWS Lake Formation (column/row-level security)
- **Compute (right engine per workload)**:
  - Spark on EC2 (Graviton + Spot) — heavy ETL/transformation
  - Athena — serverless SQL for ad-hoc exploration
  - Redshift Serverless — high-performance BI dashboards, auto-scales/pauses
- **Orchestration**: Apache Airflow (9,300+ pipelines, SLA monitoring)
- **Observability**: Cost attribution, pipeline health, data quality checks

**Migration Strategy**: 5-phase incremental (no big-bang):
1. Lakehouse foundation (S3 Tables, Glue, Lake Formation)
2. Bronze layer ingestion (raw data → Iceberg)
3. Silver layer transformation (Spark ETL)
4. Gold layer + Redshift Serverless (BI serving)
5. Cutover & validation (parallel run, compare outputs)

**Results**: 65% faster P95 queries, 63% infrastructure cost reduction, workload isolation via elastic per-engine scaling.

**Key Insight**: Single open-format data lake prevents duplication; compute scales independently per workload. Multi-engine flexibility: Spark for ETL, Athena for exploration, Redshift for BI.

---

### Configure Custom Domain Name for Amazon MSK (Aug 25, 2026)
**Topic**: Custom domain names for MSK clusters (ZooKeeper + KRaft).
- NLB + DNS + ACM certificate path
- Two-phase rollout: networking path first, then advertised listener change
- Automatic broker scaling/replacement applies config
- Available on all Provisioned clusters (Standard/Express brokers)

---

### Custom Domain Name for Amazon MSK (Technical Deep-dive)
- **Services auth flow**: EKS workload → IAM role → STS web identity token (audience: rabbitmq-iam) → broker over AMQPS 5671
- **Operators auth flow**: Keycloak SSO → broker
- **Architecture**: Resource server per OAuth provider; audience claim routes to correct signing keys

**Related Concepts**: `concepts/infrastructure/kubernetes.md`, `concepts/data-engineering/stream-processing.md`
