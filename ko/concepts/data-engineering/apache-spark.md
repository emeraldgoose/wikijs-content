---
title: Apache Spark — 개념 (번역)
description: en/concepts/data-engineering/apache-spark.md 한국어 번역 요약
published: true
tags: [concept, data-engineering, spark, ko]
locale: ko
---

# Apache Spark — 핵심 요약

## 무엇인가
대규모 데이터 처리를 위한 통합 배치+스트림 엔진. 메모리 기반 클러스터 컴퓨팅, RDD/DataFrame/Dataset API.

## 아키텍처
Driver → DAG Scheduler → Stage → Task → Executor. 장애 복구는 RDD 계보(lineage)로 수행.

## 핵심 API
- **RDD**: 저수준, 타입 안전성 낮음
- **DataFrame**: 구조화, Catalyst 옵티마이저
- **Dataset**: 타입 안전 + Catalyst

## Structured Streaming
이벤트 타임 + 워터마크로 정확히 한 번 처리. 무한 테이블로 스트림 처리.

## 성능 최적화 (세미나 체크리스트)
1. **AQE 활성화**: `spark.sql.adaptive.enabled=true`
2. **파티션 튜닝**: 128-256MB/파티션 목표
3. **브로드캐스트 조인**: 작은 테이블 (<100MB)
4. **직렬화**: Kryo + 오프힙 메모리
5. **파일 포맷**: Parquet/Delta/Iceberg

## 관련 소스
- `sources/articles/aws-bigdata.md` (레이크하우스)
- `sources/articles/netflix-techblog.md` (Kueue)
- `sources/articles/uber-engineering.md` (Hudi)
