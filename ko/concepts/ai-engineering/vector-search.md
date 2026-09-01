---
title: Vector Search — 개념 (번역)
description: en/concepts/ai-engineering/vector-search.md 한국어 번역 요약
published: true
tags: [concept, ai-engineering, vector-search, ko]
---

# 벡터 검색 — 핵심 요약

## 알고리즘
- **HNSW**: 그래프 기반, RAM, O(log N)
- **DiskANN**: 그래프(RAM) + 벡터(SSD), PQ 압축
- **PQ (Product Quantization)**: 4-8× 압축, 1-8% 재현율 손실

## 규모별 선택
| 규모 | 추천 |
|------|------|
| <1M | HNSW (RAM) |
| 1M-100M | HNSW+PQ 또는 DiskANN |
| 100M-1B+ | DiskANN/SPANN + PQ |

## 프로덕션
- 하이브리드 검색 (벡터 + 키워드 + 필터)
- 인덱스 리빌드 vs 증분 업데이트 트레이드오프
