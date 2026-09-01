---
title: Kubernetes — 개념 (번역)
description: en/concepts/infrastructure/kubernetes.md 한국어 번역 요약
published: true
tags: [concept, infrastructure, kubernetes, ko]
---

# Kubernetes — 핵심 요약

## 아키텍처
- **컨트롤 플레인**: API Server, Scheduler, Controller Manager, etcd
- **워커 노드**: kubelet, kube-proxy, 컨테이너 런타임, CNI

## 스케줄링
- 필터(프레디케이트) → 스코어(프라이어리티) → 바인드
- 고급: 토폴로지 분산, 우선순위/프리엠션, 갱 스케줄링

## 오퍼레이터 (소스에서)
- Databricks Pantheon: Rollout/Hashring/Autoscaling 컨트롤러
- Netflix Kueue: Cohort/ClusterQueue/LocalQueue 계층
