---
title: AWS Big Data — 소스 (번역 요약)
description: en/sources/articles/aws-bigdata.md 한국어 번역 요약
published: true
tags: [source, aws, data-engineering, lakehouse, ko]
locale: ko
---

# AWS Big Data Blog — 주요 기사 요약

## MSK 커스텀 도메인 (2026)
- **정적 클러스터 설정**: `custom.advertised.listeners`로 브로커별 CLI 대체
- **ZooKeeper/KRaft 동일 작동**: 스케일링/장애 복구 후에도 지속
- **2단계 롤아웃**: 1) NLB+DNS+인증서 → 2) `custom.advertised.listeners` 적용으로 자동 컷오버

## 레이저 그룹 레이크하우스 마이그레이션
- **5단계 단계적 마이그레이션**: 빅뱅 없음, Redshift+Spark 병렬 운영
- **9,300+ 파이프라인**: Airflow 관리, SLA 모니터링
- **S3 Tables 선택**: 자동 압축/스냅샷 만료/고아 파일 정리, Iceberg REST 카탈로그 API

## 컴퓨트 엔진 전략
- **Spark on EC2**: Graviton + Spot으로 비용 최적화
- **Athena**: Iceberg 서버리스 임시 SQL
- **Redshift Serverless**: BI/태블로, 자동 스케일/일시정지

## Redshift Iceberg 쓰기 지원
- UPDATE/DELETE/MERGE + CREATE/INSERT 완전 지원
- Glue Iceberg 구체화 뷰

## 참고: en/sources/articles/aws-bigdata.md (전문)
