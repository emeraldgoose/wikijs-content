---
title: Databricks Engineering — 소스 (번역 요약)
description: en/sources/articles/databricks-engineering.md 한국어 번역 요약
published: true
tags: [source, databricks, data-engineering, ai-engineering, ko]
locale: ko
---

# Databricks Engineering — 주요 기사 요약

## Pantheon: 10조 샘플/일 모니터링
- **Thanos 포크**: 160 인스턴스, 70 리전, 50억 활성 시계열
- **계층형 스토리지**: 최근 메모리, 24시간 디스크, 이후 객체 스토리지
- **메모리 보존 분할**: 장수 서비스 2시간 vs 서버리스 30분
- **Receive 그룹**: 3개 격리 StatefulSet (쿼럼 유지하며 병렬 롤아웃)
- **멀티테넌시**: 라우터에서 메트릭/레이블 검사 → 테넌트 속성
- **최소 1회 업로드**: 3개 중 2개만 업로드 (중복 감소, 내구성 유지)

## Hydra: 레이크하우스 트러블슈팅
- **PromQL→SQL 변환**: Grafana 대시보드 보존
- **Delta 직접 접근**: 배포 메타데이터/로그와 조인
- **통합 메트릭 의미**: 단일 방출 인터페이스

## Lakebase Postgres / LTAP
- **거래적 DB 기록을 S3 Parquet에**: 단일 복사본이 OLTP+OLAP 모두 서빙
- **읽기 경로**: Pageserver가 LSN 기준 객체 스토리지에서 컬럼형 읽기
- **Postgres는 분석 읽기 0**: LSN만 반환
- **CDC/미러링 아님**: 옵트인 불필요, 복제 테이블 없음, 드리프트 불가능
- **에이전트용**: DB당 에이전트/세션/브랜치, 즉시 브랜칭, PITR

## 참고: en/sources/articles/databricks-engineering.md (전문)
