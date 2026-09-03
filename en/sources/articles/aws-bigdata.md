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

---

### Query Amazon S3 Tables from Amazon EMR Trino using the Iceberg REST endpoint (Sep 2, 2026)
**Authors**: Shubham Purwar, Anirudh Chawla, Nitin Kumar, Prashanthi Chinthala

**Topic**: Querying Amazon S3 Tables from Trino on Amazon EMR via Iceberg REST catalog endpoint.

**Architecture**:
- **Trino on Amazon EMR** (v475+, EMR 7.11+) — distributed SQL engine with ANSI SQL compatibility
- **Amazon S3 Tables** — managed Apache Iceberg storage with automatic compaction, snapshot expiration, metadata management
- **Iceberg REST Catalog** — standard interface for table operations

**Implementation**:
1. Deploy via CloudFormation template (`emr-trino-s3tables.yaml`) creating EMR cluster, S3 Tables bucket, IAM roles, security groups
2. Configure Trino catalog with Iceberg REST endpoint properties:
   ```
   iceberg.rest-catalog.view-endpoints-enabled=false
   fs.hadoop.enabled=false
   fs.native-s3.enabled=true
   s3.region=us-east-1
   s3.iam-role=arn:aws:iam::<ACCOUNT-ID>:role/service-role/<ROLE-NAME>
   ```
3. Set up EMR service role trust relationships for S3 Tables access

**Key Insight**: S3 Tables eliminates operational complexity of Iceberg metadata management; Trino provides interactive query performance. Well-suited for modern data lakehouses and multi-engine analytics platforms.

**Related Concepts**: `concepts/data-engineering/apache-iceberg.md`, `concepts/data-engineering/stream-processing.md`, `concepts/infrastructure/kubernetes.md`

---

### Building Medallion Architecture with Iceberg Materialized Views in Amazon SageMaker (Sep 2, 2026)
**Topic**: Bronze → Silver → Gold medallion architecture using Iceberg materialized views with zero orchestration code.

**Architecture**:
- **Storage**: Amazon S3 Tables (managed Iceberg)
- **Compute**: Amazon Athena Spark, AWS Glue 5.1+, Amazon EMR 7.12+
- **Pattern**: Nested materialized views — each layer defined as a single SQL statement that incrementally refreshes

**Layers**:
- **Bronze**: Raw data capture (preserves original format for audit/replay)
- **Silver**: Cleaning, deduplication, type casting, business logic → validated datasets
- **Gold**: Pre-aggregated business metrics (city daily metrics, vehicle performance) via materialized views

**Key Insight**: Full pipeline creation in under 2 minutes; incremental refreshes process only changed data with no watermarks, no DAGs, no CDC plumbing. Manual refreshes billed under respective compute service pricing.

**Related Concepts**: `concepts/data-engineering/apache-iceberg.md`, `concepts/data-engineering/stream-processing.md`, `concepts/ai-engineering/feature-store.md`

---

### Build a Dynamic Streaming Data Lake with Apache Iceberg and Apache Flink (Sep 2, 2026)
**Topic**: Dynamic streaming data lake that adapts to new event types and schema changes without stopping the pipeline.

**Architecture**:
- **Managed Service for Apache Flink** — fully managed streaming applications
- **Apache Iceberg Dynamic Sink** — automatic schema evolution (existing files stay valid, new columns return null for older files)
- **Catalog**: Amazon S3 Tables or AWS Glue Data Catalog (Iceberg format v2 or v3)

**Capabilities**:
- Schema evolution without table rewrites
- New event types → new Iceberg tables appear automatically per checkpoint interval
- New fields (e.g., `userAgent`, `scrollDepth`) added as optional columns to existing tables
- Query results via Amazon Athena

**Key Insight**: Eliminates pipeline downtime for schema changes; enables streaming lakehouse with Iceberg's ACID guarantees and Flink's exactly-once processing.

**Related Concepts**: `concepts/data-engineering/stream-processing.md`, `concepts/data-engineering/apache-iceberg.md`, `concepts/data-engineering/apache-flink.md`
