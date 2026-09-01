---
title: RAG — 개념 (번역)
description: en/concepts/ai-engineering/rag.md 한국어 번역 요약
published: true
tags: [concept, ai-engineering, rag, ko]
---

# RAG — 핵심 요약

## 파이프라인
Query → 하이브리드 검색 → 리랭크 → 컨텍스트 조립 → LLM 생성 → 답변

## 검색 전략
- **밀집**: 벡터 검색 (HNSW/DiskANN)
- **희소**: BM25/키워드
- **하이브리드**: α×밀집 + β×희소 + γ×메타데이터 (프로덕션 표준)

## 컨텍스트 엔지니어링 (Netflix GenRec)
- 토큰 예산 관리: 고신호 유지, 저신호 생략, 반복 요약
- 순서: 가장 관련 높은 것 먼저
- 인용: [1], [2] 형식으로 인라인 인용

## 평가 (RAGAS)
- Faithfulness: 답변이 컨텍스트로 뒷받침되는가?
- Answer Relevancy: 쿼리에 답하는가?
- Context Recall/Precision: 관련 컨텍스트 검색되었는가?
