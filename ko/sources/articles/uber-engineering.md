---
title: Uber Engineering — 소스 (번역 요약)
description: en/sources/articles/uber-engineering.md 한국어 번역 요약
published: true
tags: [source, uber, data-engineering, ai-engineering, ko]
locale: ko
---

# Uber Engineering — 주요 기사 요약

## 비용 효율적 에이전트 코딩 (2026.08)
- **>70% PR이 로컬/클라우드 에이전트 기여**: 3,600+ 에이전트 스킬, 일 30K+ 실행
- **비용 방정식**: Users × Sessions × Turns × Requests × Tokens × Price/Token
- **단위 비용 34%↓, 세션당 비용 52%↓** (4월→8월 피크)
- **4계층 에이전트**: 특수→범용, 비용/품질/모델 선택 제어권 증가

## 최적화 레버
| 레버 | 기법 |
|------|------|
| Price/Token | 벤치마크 기반 파레토 모델 선택, 모델 기본값 |
| Tokens/Request | 400K 컨텍스트 캡, Medium 추론, 프롬프트 캐싱, MCP 호출 |
| Requests/Turn | 그래프 기반 컨텍스트, 지속적 스킬 최적화 |
| 가시성 | 실시간 비용 카운터, 지출 티어, 세션 분석 대시보드 |

## uReview (AI 코드 리뷰) 벤치마크
- 실제 PR에서 알려진 버그로 벤치마크 구성 (쉬움/중간/어려움)
- Precision/Recall/F1 + 리뷰당 비용, 지연시간, 타임아웃, 노이즈 측정
- 10개 모델 설정 중 파레토 프론티어 선택

## 내보내기 워크로드 비용 최적화 (GCS)
- **문제**: DSAR 요청이 풀 테이블 스캔 → Auto-Class 티어링 방해
- **해결**: Hudi 컬럼 통계 + 테이블 정렬
- 컬럼 통계로 데이터 파일 없이 프루닝, 정렬로 min/max 범위 타이트하게

## COUNT(DISTINCT) 스케일링 (2년간 288억 고유 ID)
- **실패**: Bitmap-32 (사전 SPOF), Bitmap-64 (2GB UDAF 제한), HLL (1-5% 오차)
- **해결**: 청크드 집계 버퍼 (상위 16비트 해시로 65,536 파티션)
- Chernoff bound로 청크 크기 안전성 검증
- 2년 백필 65% 단축, OOM 완전 제거

## 참고: en/sources/articles/uber-engineering.md (전문)
