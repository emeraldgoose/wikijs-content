---
title: Uber Engineering — Source (Full Body)
description: Uber Engineering blog — full-body summaries for seminar preparation
published: true
tags: [source, uber, data-engineering, ai-engineering, software-factory, hudi, lakehouse, count-distinct]
---

# Uber Engineering

Feed: https://www.uber.com/blog/engineering/ (tier 2)

## Articles Read (Full Body)

### Running a Software Factory Efficiently at Uber Scale (Aug 27, 2026)
**Author**: Uday Kiran Medisetty (Distinguished Engineer)

**Context**: 70%+ PRs attributed to AI agents; 3,600+ agent skills; 30K+ agent executions/day.

**Growth (Feb–Aug 2026)**: Weekly active users 7x, agent requests 9.4x, total AI spend stabilized (optimizations).

**Cost Equation** (6 terms):
```
Total Spend = Users × Sessions/User × Turns/Session × Requests/Turn × Tokens/Request × Price/Token
```

**Metrics by Layer**:
| Layer | Metrics | Answers |
|-------|---------|---------|
| Portfolio | Total cost, distinct users, per-tool cost | Where money goes |
| Unit Economics | Cost/user, req/user, cost/1K req, tokens/req, cost/1M tokens, cost/session | Tool getting cheaper? |
| Model Economics | Cost per model, cost/1K req, cost/1M tokens | Model releases changing bill? |
| Driver Decomposition | Adoption, engagement, input/output workload | Why number moved? |
| Managed Agent Outcomes | Cost/merged PR, cost/review, cost/alert, quality (revert rate, F1, MTTR) | Cheaper per value unit? |

**Optimization Levers**:
- **Price/Token**: Pareto-optimal model selection (benchmark-driven), model defaults
- **Tokens/Request**: 400K context cap, Medium reasoning, Prompt Caching, Tool search/CLI-resolved MCP, Code-mode batching, Gateway-routed SaaS MCPs
- **Requests/Turn**: Graph-grounded context, Continuous Skill Optimization
- **Visibility**: Live cost counter, spend tiers, session analysis dashboard

**Benchmark-Driven Model Selection** (4 steps):
1. Define workload benchmark (real PRs with known bugs, graded easy/medium/hard)
2. Score: precision, recall, F1, cost/PR, latency, timeouts, noise
3. Pareto frontier: cost vs quality
4. Deploy Pareto-optimal config

**uReview Example**: Switching models improved F1 while dramatically reducing cost/PR. Pareto frontier visualization guides selection.

---

### Running Cost-Efficient Export Workloads at Uber (Aug 12, 2026)
**Authors**: Pankaj Mohapatra, Arun Mahadeva Iyer, Balajee Nagasubramaniam

**Problem**: Export workloads (DSAR, compliance, privacy) — small result sets from large historical datasets. On GCS-backed lakehouse, full-table scans keep data hot, preventing auto-class tiering.

**Solution**: Apache Hudi Column Stats + Table Sorting
- **Column Stats**: Metadata-table level min/max/null/count per column → file pruning without reading Parquet footers
- **Sorting**: Cluster predicate column (user ID) → tighter min/max ranges → more selective pruning

**Results**: Benchmark on real partition:
- Disk reduction: 24.8%
- File pruning effective across low/mid/high predicate counts
- Reduced GCS egress, Class B operations, latency

**Key Insight**: Column stats move pruning metadata to table level (avoids footer reads that keep files hot). Sorting improves pruning effectiveness.

---

### Scaling Exact COUNT(DISTINCT) for High-Cardinality Non-Rollup Metrics (Jul 30, 2026)
**Authors**: Prakhar Agarwal, Avinash Varma Sagi, Abhay Singh Chauhan

**Problem**: Non-rollup metrics (MAU, quarterly retention) — exact distinct count of 3.6B UUIDs at quarterly scale. RoaringBitmap hits JVM 2GB array limit at ~179M unique identifiers.

**Failed Approaches**:
- Bitmap-32 + Global Dictionary: single point of failure, sequential backfills
- Bitmap-64 Monolithic: 2GB JVM array limit breached at 179M
- HyperLogLog: 1-5% error unacceptable for financial reporting

**Solution**: Chunked Aggregation Buffer Strategy
- Partition bitmap aggregation buffer: `Map<Integer, Roaring64Bitmap>` keyed by top 16 bits of xxHash64
- `chunkId = (int)(hash >>> 48)` — 65,536 chunks
- Average 55K values/chunk at 3.6B scale; Chernoff bound confirms OOM probability ~zero
- 16-bit sweet spot: 8 bits = insufficient headroom; 24 bits = map overhead/GC pressure

**Benefits**:
- Eliminates 2GB JVM constraint entirely
- Enables concurrent backfill execution (no shared dictionary)
- Self-describing partial results: 0xDEADBEEF magic number
- Streaming serialization (no monolithic byte[])

**Deployed**: 75 metric families; 65% backfill time reduction; zero OOM failures.

---

## Related Concepts
- `concepts/data-engineering/apache-spark.md` (Spark UDAF, aggregation state)
- `concepts/data-engineering/stream-processing.md` (real-time metrics)
- `concepts/ai-engineering/agent.md` (software factory agentic workflows)
