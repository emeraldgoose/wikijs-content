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

---

## Query Amazon S3 Tables from EMR Trino via Iceberg REST (2026-09-02)
- **핵심**: Trino(EMR 7.11+) + S3 Tables + Iceberg REST 카탈로그 연동
- **CloudFormation**으로 EMR 클러스터, S3 Tables 버킷, IAM 역할 일괄 배포
- **Trino 카탈로그 설정**: `fs.native-s3.enabled=true`, `iceberg.rest-catalog.view-endpoints-enabled=false`
- **운영 단순화**: S3 Tables가 압축/스냅샷/메타데이터 자동 관리 → 레이크하우스에 적합

## Iceberg 구체화 뷰로 메달리온 아키텍처 구축 (2026-09-02)
- **Bronze→Silver→Gold** 3계층을 **중첩 구체화 뷰** 3개 SQL로 구현, 오케스트레이션 코드 없음
- **S3 Tables** + Athena Spark / Glue 5.1+ / EMR 7.12+
- **증분 리프레시**: 변경된 데이터만 처리, 워터마크/DAG/CDC 불필요
- **파이프라인 생성 <2분**, 수동 리프레시는 각 컴퓨트 서비스 요금제 적용

## Iceberg + Flink로 동적 스트리밍 데이터 레이크 (2026-09-02)
- **Flink 관리형 서비스** + **Iceberg Dynamic Sink**로 스키마 진화 자동 처리
- **기존 파일 유효 유지**, 새 컬럼은 과거 파일에 null 반환
- **새 이벤트 타입** → 체크포인트 주기마다 새 Iceberg 테이블 자동 생성
- **Athena**로 쿼리 가능, 파이프라인 중단 없이 스키마 변경 대응
