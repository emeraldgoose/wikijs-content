---
title: Spotify Engineering — Source (Full Body)
description: Spotify Engineering RSS feed — full-body summaries for seminar preparation
published: true
tags: [source, rss, spotify, data-engineering, ai-engineering, ab-testing, data-lake]
locale: en
---

# Spotify Engineering

Feed: https://engineering.atspotify.com/feed/ (tier 1)

## Articles Read (Full Body)

### When Can LLMs Replace Humans in A/B Tests? (Aug 13, 2026)
**TL;DR**: LLM predictions can stand in for human outcomes in A/B tests, but only by assumption, not by design.

**Key insight**: LLMs as simulators for A/B testing requires strong assumptions about human behavior alignment. Not a design guarantee — empirical validation needed.

**Related**: `concepts/machine-learning/transformer.md`, `concepts/ai-engineering/agent.md`

---

### Indexing the Data Lake for Online Point Queries (Jul 27, 2026)
**Problem**: Vast quantities of data at low latency for online services.

**Solution**: Lakehouse indexing strategy for online point queries. Architecture decisions for balancing throughput, latency, and freshness.

**Related**: `concepts/data-engineering/delta-lake.md`, `concepts/data-engineering/apache-spark.md`

---

### Content Ingestion & Podcast Video Incident Report (Jul 20, 2026)
**Reliability incident**: Podcast creators experienced reliability issues over 2 months.

**Root cause analysis**: Incident report with post-mortem, remediation steps, and preventive measures.

**Related**: `concepts/infrastructure/kubernetes.md`, `guides/infrastructure/deploy-kubernetes.md`

---

### Encoding Your Domain Expert: The Context Layer Behind Spotify's Data Assistant (Jun 10, 2026)
**Pattern shift**: From dashboard lookup → domain expert encoded as context layer for AI data assistant.

**Technique**: Context engineering for LLM-based data assistant; encoding domain knowledge into prompts/context.

**Related**: `concepts/ai-engineering/rag.md`, `concepts/ai-engineering/agent.md`

---

### Coding Is No Longer the Constraint: Scaling Developer Experience to Teams and Agents (Jun 3, 2026)
**Chief architect**: Scaling developer experience to both teams and AI agents.

**Focus**: How Spotify makes teams and AI agents more effective; developer productivity at scale with agentic workflows.

**Related**: `concepts/ai-engineering/agent.md`, `guides/ai-engineering/build-agent.md`
