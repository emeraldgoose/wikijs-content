---
title: Netflix Tech Blog — Source (Full Body)
description: Netflix Tech Blog RSS feed — full-body summaries of recent articles for seminar preparation
published: true
tags: [source, rss, netflix, data-engineering, ai-engineering, recommendation, multimodal, kueue]
---

# Netflix Tech Blog

Feed: https://netflixtechblog.com/feed (tier 1)

## Articles Read (Full Body)

### MAPS: Netflix's Multimodal Asset Personalization at Scale (Aug 28, 2026)
**Authors**: Emma Yanyang Kong, Aditya Deshpande, Asad Abbasi, Bowei Yan, David Fagnan, Ashish Rastogi, Dhaval Patel, Ray Zhang

**Problem**: Cold-start for new title assets (artwork, video previews). Traditional models treat assets as opaque IDs; no interaction data = no personalization.

**Solution**: Multimodal embeddings (CLIP for artwork, SeqCLIP/MediaFM for video) via Netflix Embedding Store.
- Concatenate CLIP image embedding (768-dim) with learned ID embedding → MLP → asset representation
- **Cross-canvas transfer**: CLIP embeddings invariant to crop/resize/aspect ratio → single unified model replaces 5 per-canvas models
- **Reward-weighted training**: Weight training examples by long-term reward (play, thumbs-up) rather than raw impression counts
- **IPS evaluation**: Inverse Propensity Scoring on exploration traffic for unbiased offline evaluation

**Results**: Ablation shows V3 (unified + embeddings) wins on data-starved canvases; cold-start shifts from blind spot to informed opinion.

---

### GenRec: Towards LLM-Native Recommendation at Netflix (Jul 30, 2026)
**Authors**: Ying Li, Arjun Rao, Shradha Sehgal

**Architecture**: Two-phase training
1. **Phase 1**: Netflix-adapted foundation LLM (content understanding, member behavior, language)
2. **Phase 2**: Post-train for ranking with reward-weighted losses, catalog-aware scoring head

**Context Engineering**: Token budget management — retain high-signal (long plays, thumbs-up), omit low-signal (short plays), summarize repetitive (binge), elaborate cold-start items.

**Serving**: Prefill-only vLLM for cost efficiency.

**A/B Results**: Statistically significant improvement vs mature production ranker; fraction of Phase-2 data/signals; shift from feature engineering to context engineering.

---

### How Netflix Simplified Batch Compute with Kueue (Jun 22, 2026)
**Authors**: Multiple

**Migration**: Millions of batch jobs from custom scheduler to Kueue (Kubernetes job queueing).
- Cohort/ClusterQueue/LocalQueue hierarchy for tenant management
- API parity maintained during migration (no disruption)
- Migrated largest/complex customer first (derisked)
- Preemption-based fair sharing: lend idle reservation capacity, preempt lower-priority for higher-priority

**Results**: Kueue fully rolled out; millions of workloads managed; increased resource utilization; production migration in 4 weeks.

---

### In-House LLM Serving at Netflix (Jul 17, 2026)
**Topics**: Engine selection, model packaging, API design, deployment strategy, output constraints enforcement.
- JVM-based unified serving system (routing, A/B test, candidate generation, feature fetching, inference, post-processing)
- Small CPU models in-process; large models → remote Model Scoring Service (MSS)
- Versioned deployments: independent (modelId, modelVersion) pairs; overlap transition solves I/O schema change coordination gap

---

### Building Service Topology at Scale (Jul 13, 2026)
**Multi-layer**: Network (eBPF), IPC metrics, distributed tracing → physically separate graph layers
- Kafka consumers fell behind, OOM, 100x traffic skew, GC pauses
- Immutable data structures → GC pressure at millions records/sec
- Hash-based partition redistribution on ASG scale changes
- Real-time topology updates (tens of minutes) vs hour-old batch

---

### GenPage: Generative Homepage Construction (Jun 29, 2026)
- RL post-training increased homepage diversity without explicit diversity objective
- Daily incremental updates: latest day + sampled past data to avoid catastrophic forgetting
- Pretraining on "Netflix homepage language" provides strong initialization (mirrors LLM pretrain→post-train)
- Scaling: 120M→900M params, losses decrease power-law

## Related Concepts
- `concepts/data-engineering/apache-spark.md` (Kueue batch orchestration, Spark on EC2)
- `concepts/ai-engineering/rag.md` (multimodal embeddings, context engineering)
- `concepts/machine-learning/attention.md` (transformer-based ranking)
