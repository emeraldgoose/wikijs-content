---
title: Netflix Tech Blog — 소스 (번역 요약)
description: en/sources/articles/netflix-techblog.md 한국어 번역 요약
published: true
tags: [source, netflix, data-engineering, ai-engineering, ko]
---

# Netflix Tech Blog — 주요 기사 요약

## GenRec: LLM 네이티브 추천 시스템
- **CLIP 임베딩** (768차원) + 학습된 ID 임베딩 → 자산 표현 `h_a`
- **콜드 스타트 해결**: 새 타이틀 자산에 즉시 개인화 가능 (시각/재능/색상 선호도 전이)
- **단일 통합 모델**: 5개 캔버스별 모델 → 1개 (CLIP 불변성 활용)
- **보상 기반 가중치**: 상호작용 유형별 장기 보상 `ρ`로 가중
- **IPS 오프라인 평가**: 탐색 트래픽에서 편향 없는 보상 추정
- **Prefill-only vLLM**: 랭킹용 디코딩 없이 프리필만 (지연시간 ↓)

## MAPS: 멀티모달 자산 개인화
- Netflix MAPS (Multimodal Asset Personalization at Scale)
- SeqCLIP, MediaFM으로 비디오/이미지 임베딩

## Kueue on Kubernetes
- 배치 + Kueue 마이그레이션: API 호환성 유지 (위험 분산)
- 가장 복잡한 고객부터 마이그레이션 (4주 완성)
- 공정 공유/프리엠션: `reclaimWithinCohort: Any`

## 아트워크 모델 통합
- CLIP 임베딩은 크롭/리사이즈/종횡비 불변 → 동일 소스 이미지에 근접 벡터
- 신호 풀링으로 데이터 부족 캔버스에서 큰 이득

## 참고: en/sources/articles/netflix-techblog.md (전문)
