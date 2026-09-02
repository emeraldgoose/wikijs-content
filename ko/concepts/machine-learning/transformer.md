---
title: Transformer — 개념 (번역)
description: en/concepts/machine-learning/transformer.md 한국어 번역 요약
published: true
tags: [concept, machine-learning, transformer, ko]
locale: ko
---

# Transformer — 핵심 요약

## 아키텍처
Encoder/Decoder 레이어: Multi-Head Self-Attention → Add&Norm → Feed-Forward → Add&Norm

## 스케일링 법칙 (소스에서)
- Netflix GenRec: 2단계 훈련 (Foundation → Ranking post-train)
- HuggingFace Unified Dynamics: 훈련=상태 가진 파라미터-옵티마이저 시스템 진화
- JIT-Agent: 하네스 지능이 모델 스케일링과 직교

## 핵심 최적화
- FlashAttention (IO-aware, 정확함)
- KV Cache (디코딩 시 재사용)
- 양자화: FP8, INT4, GPTQ
- Prefill-only serving (Netflix: 랭킹용)
