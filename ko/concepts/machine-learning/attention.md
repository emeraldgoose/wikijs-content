---
title: Attention — 개념 (번역)
description: en/concepts/machine-learning/attention.md 한국어 번역 요약
published: true
tags: [concept, machine-learning, attention, ko]
locale: ko
---

# Attention — 핵심 요약

## 핵심
`Attention(Q,K,V) = softmax(Q·K^T/√d_k)·V` — O(N²) 복잡도

## 변종
- **FlashAttention**: 타일링+재계산으로 정확한 O(N) 메모리
- **KV Cache**: 디코딩 시 키/값 재사용
- **Sparse/Linear**: Longformer, Performer, RWKV

## 소스에서
- PonderPounce: MLLM 인과적 컨텍스트(KV 캐시)를 에피소드 메모리로 사용
- Unified Dynamics: Attention이 "조직 조건" 실현
