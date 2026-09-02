---
title: Databricks Engineering — Source (Full Body)
description: Databricks Engineering blog — full-body summaries for seminar preparation
published: true
tags: [source, databricks, data-engineering, monitoring, lakehouse, postgres, lakebase]
locale: en
---

# Databricks Engineering

Feed: https://databricks.com/blog/category/engineering (tier 2)

## Articles Read (Full Body)

### 10 Trillion Samples a Day: Scaling Beyond Traditional Monitoring Infra (May 5, 2026)
**Authors**: David Yuan, Yi Jin, Karan Bavishi, HC Zhu, Joey Beyda

**Scale**: 5B active timeseries, 10T samples/day, 70 cloud regions across 3 clouds.

**Key Problems Solved**:

1. **Pantheon TSDB (Thanos fork)**:
   - 160+ Thanos instances across all regions
   - Tiered storage: in-memory (recent) → disk (24h) → object storage (historical)
   - Two Receive groups with distinct memory-retention: persistent services (2h), ephemeral serverless (30min)
   - Three isolated StatefulSets per group (quorum writes, parallel rolling updates)
   - Multitenancy: rule-based tenant attribution by metric name/labels
   - At-least-once uploads: only 2 of 3 StatefulSets upload to object storage
   - Control plane: Rollout Operator, Hashring Controller, Autoscaling/Self-Healing Controller
   - **Results**: Millions $ saved, 5x downtime reduction, eliminated manual toil

2. **Cardinality Aggregation**:
   - Serverless VM launches (tens of millions daily) → label cardinality explosion
   - Automated aggregation: drop expensive labels (pod ID) during ingestion, keep fleetwide view
   - "Bend the curve" of cardinality growth

3. **Hydra: Lakehouse-based Troubleshooting Platform**:
   - High-cardinality metrics → Delta tables in Lakehouse
   - **Grafana PromQL → SQL**: PromQL-to-SQL conversion layer translates PromQL to Delta table queries
   - **Direct SQL Access**: Delta tables exposed in Databricks SQL/notebooks for joins with deployment metadata, logs, anomaly detection
   - **Unified Metric Semantics**: Same interface whether TSDB-aggregated or Lakehouse-raw path
   - Engineers emit once; platform handles aggregation, raw preservation, routing

---

### Object Storage + WAL: Lakebase Postgres for the Agentic Era (Aug 27, 2026)
**Authors**: Cassie Murray, Carlota Soto

**Core Idea**: Decouple compute and storage in Postgres; treat WAL on object storage (S3) as source of truth.

**Architecture**:
- **Compute Layer**: Standard Postgres (parses SQL, plans, MVCC, locks, indexes). RAM for buffers, NVMe for page cache. Can start/stop/scale/die without durability risk.
- **Storage Layer**:
  - **Safekeepers**: Replicate WAL via Paxos-based protocol; quorum ack = commit
  - **Pageserver**: Turns WAL into pages; materializes page versions → object storage (async)
  - **Object Storage**: Immutable history in open columnar formats (append-only, never in-place updates)

**Write Path**: Postgres generates WAL → streams to safekeepers → quorum ack commits → page materialization async (off critical path)
**Read Path**: `GetPage@LSN` — RAM → NVMe → pageserver (reconstructs from layers) → caches locally
- Pageserver never updates files in place (image layers + delta layers); perfect for object storage
- Background compaction reshuffles layers; garbage collects outside retention window

**Agent-Friendly Features**:
- Instant database branching (pointer to LSN)
- Point-in-time restores (read at historical LSN)
- Time-travel queries
- Database per agent/session/branch affordable (stops drawing compute cost when idle)

**LTAP (Lake Transactional/Analytical Processing)**:
- One durable copy in open columnar formats for both OLTP + OLAP
- Analytical query: get current LSN (cheap metadata), read majority from object storage, fetch recent unmaterialized changes from pageserver
- No CDC/replication drift — table already exists in lake

---

## Related Concepts
- `concepts/data-engineering/apache-spark.md` (monitoring infrastructure, Delta Lake)
- `concepts/infrastructure/kubernetes.md` (StatefulSets, control plane)
- `concepts/ai-engineering/agent.md` (Lakebase for agentic workloads)
