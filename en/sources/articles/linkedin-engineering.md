---
title: LinkedIn Engineering — Source (Full Body)
description: LinkedIn Engineering blog — full-body summaries for seminar preparation
published: true
tags: [source, linkedin, data-engineering, infrastructure, feed, ml]
locale: en
---

# LinkedIn Engineering

Feed: https://www.linkedin.com/blog/engineering/feed (tier 2)

## Articles Read (Full Body)

### Engineering the Next Generation of LinkedIn's Feed (Mar 12, 2026)
**Author**: Hristo Danchev

**Focus**: Transformation of LinkedIn's overarching search experience and feed tech stack. Scalable LLM-based stack for smarter, faster, more personalized experience.

**Key areas**: Feed ranking, content appearance, member relevance, LLM integration at scale.

---

### FishDB: A Generic Retrieval Engine for Scaling LinkedIn's Feed (Nov 17, 2025)
**Author**: Kenneth Li

**Problem**: Scaling feed retrieval at LinkedIn scale.

**Solution**: FishDB — generic retrieval engine. Architecture for high-throughput, low-latency retrieval across massive datasets.

**Related**: `concepts/data-engineering/stream-processing.md`, `concepts/infrastructure/kubernetes.md`

---

### Java Heap Memory and GC Tuning for High-Performance Services (Sep 13, 2024)
**Author**: Nisheedh Raveendran

**Deep dive**: JVM heap management, garbage collection tuning for high-performance services at LinkedIn scale.

**Practical**: GC algorithms, heap sizing, pause time optimization, monitoring.

---

### How LinkedIn Built the Engineering Infrastructure to Ignite Professional... (Nov 20, 2023)
**Author**: Shweta Patira

**Generative AI infrastructure**: Building the platform foundation for GenAI at LinkedIn scale.

**Focus**: Infrastructure for training, serving, and integrating LLMs into professional products.

---

### Homepage Feed Multi-Task Learning using TensorFlow (Jun 3, 2021)
**Author**: Ian Ackerman

**Multi-task learning**: TensorFlow-based approach for homepage feed ranking with multiple objectives.

**Technique**: Shared representations across tasks, task-specific heads, joint optimization.

---

## Related Concepts
- `concepts/data-engineering/stream-processing.md` (FishDB retrieval, feed infrastructure)
- `concepts/machine-learning/transformer.md` (LLM-based feed stack)
- `concepts/ai-engineering/rag.md` (retrieval engine architecture)
