---
title: SHAPE of Chain-of-Thought in Math Reasoning
description: HuggingFace Daily Papers — 2026-06-28 — Seoul National University
published: true
tags: [source, paper, huggingface, seoul-national-university]
locale: en
arxiv_id: 2608.28600
---

# SHAPE of Chain-of-Thought in Math Reasoning

**arXiv**: 2608.28600 | **Published**: 2026-06-28 | **Organization**: Seoul National University | **Submitted by**: Minjae Oh | **Upvotes**: 27

**Authors**: Jonghyun Song, Sangjun Song, Minjae Oh, Haesung Pyun, Sungsik Lee, Yohan Jo

## Abstract

Large language models (LLMs) achieve strong performance on mathematical reasoning benchmarks, yet the mathematically meaningful skills underlying their reasoning remain underexplored. We introduce SHAPE, a framework that analyzes Chain-of-Thought (CoT) trajectories through two lenses developed in mathematics education: (1) semantic spaces: the model's evolving mathematical interpretations of a problem (e.g., algebraic, geometric), and (2) heuristics: the specific mathematical actions taken within those spaces (e.g., simplifying the problem, working backward). We first use SHAPE to analyze the reasoning patterns of various models. Our findings reveal that the mathematical heuristics employed by a model better explain final answer correctness than traditional CoT features. Furthermore, models are likely to reach correct solutions by concentrating their reasoning effort within a few semantic spaces rather than exploring many disparate ones -- a pattern consistent with human behavior. Next, we utilize the SHAPE lens to evaluate whether post-training truly enhances mathematical proficiency. We find that reinforcement learning induces mode-seeking in heuristic usage. Lastly, we post-train LLMs by promoting diverse heuristics and demonstrate its effectiveness in improving accuracy. Overall, SHAPE provides a theoretically-grounded diagnostic framework for decoding LLM reasoning and offers a new path toward post-training LLMs for math reasoning. The code for our model is available at https://github.com/holi-lab/SHAPE-of-CoT

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

- arXiv: https://arxiv.org/abs/2608.28600
- HuggingFace: https://huggingface.co/papers/2608.28600
