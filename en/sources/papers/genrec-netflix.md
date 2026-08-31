---
title: GenRec — Paper Source (Netflix)
description: Full-body seminar summary of Netflix GenRec paper (LLM recommendation ranker)
published: true
tags: [paper, source, netflix, llm, recommendation, ai-engineering]
---

# GenRec: Towards LLM-Native Recommendation at Netflix

Full body read (not abstract only). Seminar-level summary for SW engineers.

Core idea: Replace thousands of hand-engineered features with verbalized user/item text + post-trained LLM ranker.

Architecture (two-phase):
1. Foundation LLM (Netflix-adapted) — content + behavior understanding
2. GenRec (post-training) — ranking objective + reward-weighted loss + catalog-aware scoring head

Context engineering: fixed token budget; retain high-signal, omit low-signal, summarize repetitive (e.g., binge-watching).

Serving: prefill-only vLLM on Netflix LLM stack for cost efficiency.

Results (A/B test): statistically significant improvement vs mature production ranker; uses only fraction of Phase-2 data/signals.

Implication: shift from feature engineering to context engineering.
