---
title: DICS: Exploring Data Intrinsic Consistency for Visual Instruction Selection
description: HuggingFace Daily Papers — 2026-08-31 — SpatialAxiom
published: true
tags: [source, paper, huggingface, spatialaxiom]
locale: en
arxiv_id: 2608.30209
---

# DICS: Exploring Data Intrinsic Consistency for Visual Instruction Selection

**arXiv**: 2608.30209 | **Published**: 2026-08-31 | **Organization**: SpatialAxiom | **Submitted by**: hongyuyang | **Upvotes**: 2

**Authors**: Yuyang Hong, Jinhui Guo, Jiaqi Gu, Lubin Fan, Ruixiang Wang, Kun Ding, Yue Wu, Shiming Xiang, Jieping Ye

## Abstract

Visual instruction tuning is crucial for advancing the vision-language alignment and instruction-following capabilities of Vision-Language Models (VLMs). However, identifying optimal subsets under a fixed ratio constraint from rapidly expanding datasets remains a significant bottleneck. While existing methods largely depend on distribution diversity or heuristic filtering, they often overlook the internal coherence within individual samples. To bridge this gap, we propose Data Intrinsic Consistency (DIC), a self-scoring metric designed to quantify the sample-level inter-component consistency. DIC consists of two modules: Visual Information Consistency (VIC), evaluating the alignment between visual content and instructions, and Response Information Consistency (RIC), assessing response coherence relative to the instruction. Building upon DIC, we introduce Data Intrinsic Consistency Selection (DICS), an adaptive data selection method that optimizes the trade-off between high intra-sample consistency and global distributional diversity under varying data budgets. Extensive experiments demonstrate that DICS consistently outperforms state-of-the-art methods across diverse dataset scales and model architectures, surpassing full-dataset fine-tuning while using only 25% of the LLaVA-1.5-665K data. We further curate DICS-6M, a 6M-sample multi-modal instruction corpus that enables the largest-scale visual instruction selection study to date; remarkably, DICS reaches 94.52\% of the official InternVL3-8B-Instruct performance using less than 25\% of its reported training data. Code can be seen at https://github.com/cqu-student/DICS

## Key Contributions

- [To be filled after full paper reading]

## Methodology

- [To be filled after full paper reading]

## Results

- [To be filled after full paper reading]

## Relevance to Software Engineers

- [To be filled: practical implications for SW engineers]

## Related Concepts

- `concepts/ai-engineering/agent.md`
- `concepts/ai-engineering/llm-training.md`
- `concepts/machine-learning/transformer.md`

## References

- arXiv: https://arxiv.org/abs/2608.30209
- HuggingFace: https://huggingface.co/papers/2608.30209
