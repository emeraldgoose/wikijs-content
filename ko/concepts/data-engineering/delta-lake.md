---
title: Delta Lake — 개념 (번역)
description: en/concepts/data-engineering/delta-lake.md 한국어 번역 요약
published: true
tags: [concept, data-engineering, delta-lake, ko]
locale: ko
---

# Delta Lake — 핵심 요약

## 핵심 기능
- ACID 트랜잭션 (옵티미스틱 동시성 제어)
- 시간 여행 (버전/타임스탬프 쿼리)
- 스키마 진화 (mergeSchema, overwriteSchema)
- DML: MERGE, UPDATE, DELETE, INSERT

## 최적화
- `OPTIMIZE table ZORDER BY (col)` — 파티션 + Z-오더링
- `VACUUM table RETAIN 168 HOURS` — 파일 정리

## Iceberg와 비교
- Iceberg: 파티션 진화, 숨김 파티셔닝 더 유연
- Delta: Databricks/Spark 통합 더 타이트
