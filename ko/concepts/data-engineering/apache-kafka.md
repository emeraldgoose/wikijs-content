---
title: Apache Kafka — 개념 (번역)
description: en/concepts/data-engineering/apache-kafka.md 한국어 번역 요약
published: true
tags: [concept, data-engineering, kafka, ko]
---

# Apache Kafka — 핵심 요약

## 무엇인가
분산 이벤트 스트리밍 플랫폼. 로그 구조, 파티션, 복제된 커밋 로그.

## 핵심 개념
- **토픽**: 파티션된 순서 있는 레코드 시퀀스
- **파티션**: 오프셋으로 순서 보장
- **브로커**: 리더/팔로워 복제
- **컨슈머 그룹**: 병렬 소비, 파티션당 1 컨슈머

## 성능 최적화
- `linger.ms=5`, `batch.size=65536`, `compression.type=lz4`
- `acks=all` + `enable.idempotence=true` = 정확히 한 번

## 관련 소스
- `sources/articles/uber-engineering.md` (Hudi ingestion)
- `sources/articles/netflix-techblog.md` (실시간 그래프)
- `sources/articles/twitter-engineering.md` (Sparrow)
