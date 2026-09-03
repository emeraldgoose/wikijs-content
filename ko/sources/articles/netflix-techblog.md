---
title: Netflix Tech Blog — 소스 (번역 요약)
description: en/sources/articles/netflix-techblog.md 한국어 번역 요약
published: true
tags: [source, netflix, data-engineering, ai-engineering, ko]
locale: ko
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

---

## 2026년 추가 기사 요약

### Flink 오토스케일러 비교: 반응형 vs 예측형 (2026-08-21)
- **반응형**: 백로그/지연 지표 기반 (Kueue + HPA)
- **예측형**: 과거 패턴 + ML로 부하 예측, 스파이크 전 사전 스케일링
- **결과**: 예측형이 트래픽 스파이크 시 SLA 위반 60% 감소
- **하이브리드**: 베이스라인은 예측형, 이상치는 반응형

### 실시간 분산 그래프 Part 3: gRPC 쿼리 레이어 (2026-08-07)
- GraphQL 게이트웨이 → gRPC 서비스 → 분산 그래프 스토리지 (Cassandra + 커스텀 인덱스)
- 쿼리 최적화: 프레디케이트 푸시다운, 병렬 팬아웃, 결과 병합
- 읽기-쓰기 일관성: 버전 기반 읽기; 크로스 리전은 최종적 일관성
- 성능: 1-hop 쿼리 P99 < 50ms, 파티션 샤딩으로 수평 확장

### 디바이스 역량 통합 모델링 (2026-07-31)
- 수천 개 디바이스 모델의 다양한 역량(코덱, DRM, 화면, CPU) 통합
- 계층적 역량 분류학 + UA/텔레메트리 기반 ML 추론
- 역량 벡터: 코덱 지원, 최대 해상도, HDR, DRM, 메모리 클래스
- 적용: 적응형 비트레이트, 코덱 협상, UI 레이아웃 최적화

### 제어 가능한 AI 비디오 편집: 초기 연구 탐색 (2026-06-23)
- 제어 신호: 텍스트 프롬프트 + 공간 마스크 + 모션 궤적 + 스타일 레퍼런스
- 아키텍처: 비디오 디퓨전 백본에 ControlNet 스타일 어댑터
- 과제: 시간적 일관성, 세밀한 제어, 컴퓨트 비용
- 상태: 초기 연구 단계, 프로덕션 파이프라인 미적용
