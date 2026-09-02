---
title: Stream Processing — 개념 (번역)
description: en/concepts/data-engineering/stream-processing.md 한국어 번역 요약
published: true
tags: [concept, data-engineering, stream-processing, ko]
locale: ko
---

# 스트림 처리 — 핵심 요약

## 핵심 개념
- **이벤트 타임 vs 처리 타임**: 워터마크로 지연 데이터 처리
- **윈도우**: 텀블링/호핑/세션/글로벌
- **상태**: 키드 상태 + 체크포인팅 (정확히 한 번)

## 프레임워크 비교
| | Flink | Spark Structured Streaming | Kafka Streams |
|--|-------|---------------------------|---------------|
| 이벤트 타임 | 네이티브 | 네이티브 | 네이티브 |
| 지연시간 | ~ms | ~100ms | ~ms |

## 소스별 패턴
- Netflix: eBPF → Kafka → 멀티레이어 토폴로지 (수천만 레코드/초)
- Twitter: Sparrow 배치→스트리밍 전환
- Uber: Hudi 컬럼 통계로 파일 프루닝
