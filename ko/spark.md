---
title: Spark
description: Apache Spark 소개와 핵심 개념
published: true
date: 2026-08-31T11:35:00.000Z
tags: [spark, data-engineering, big-data]
editor: markdown
dateCreated: 2026-08-31T11:35:00.000Z
---

# Apache Spark

> 빠른 대용량 데이터 처리를 위한 오픈소스 통합 분석 엔진

## 개요

**Apache Spark**는 메모리 기반 클러스터 컴퓨팅 프레임워크로, Hadoop MapReduce보다 최대 100배 빠른 처리 속도를 목표로 설계되었습니다.

## 핵심 구성 요소 {.tabset}

### Spark Core
- **RDD** (Resilient Distributed Dataset): 불변 분산 데이터 집합
- **DAG** (Directed Acyclic Graph): 작업 최적화 그래프

### Spark SQL
구조화된 데이터 쿼리를 위한 DataFrame / Dataset API

### Spark Streaming / Structured Streaming
실시간 스트림 처리

## 예시 코드

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("Example").getOrCreate()
df = spark.read.csv("data.csv", header=True)
df.groupBy("category").count().show()
```

## 참고
- [공식 문서](https://spark.apache.org/docs/latest/)
- 사용 언어: Scala, Java, Python, R
