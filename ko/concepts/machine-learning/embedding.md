---
title: Embedding — 개념 (번역)
description: en/concepts/machine-learning/embedding.md 한국어 번역 요약
published: true
tags: [concept, machine-learning, embedding, ko]
locale: ko
---

# Embedding — 핵심 요약

## 종류
- 텍스트: BERT, E5/BGE, LLM 히든 스테이트
- 이미지/비디오: CLIP, SeqCLIP, MediaFM (Netflix MAPS)
- 멀티모달: Netflix Embedding Store (단일 저장소)

## 벡터 검색
- HNSW (RAM, <100M), DiskANN (SSD, >100M)
- 하이브리드: 벡터 + BM25 + 메타데이터 필터

## Netflix Embedding Store
- 훈련/서빙 동일 임베딩 → 스큐 없음
- CLIP 불변성 → 5개 캔버스 단일 모델
