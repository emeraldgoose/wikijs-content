---
title: Service Mesh — 개념 (번역)
description: en/concepts/infrastructure/service-mesh.md 한국어 번역 요약
published: true
tags: [concept, infrastructure, service-mesh, ko]
---

# Service Mesh — 핵심 요약

## 아키텍처
- **데이터 플레인**: 사이드카 프록시 (Envoy) — 트래픽 가로채기/라우팅/관찰
- **컨트롤 플레인**: 정책/설정 배포 (Istiod, Linkerd Control Plane)

## 핵심 기능
- **트래픽 관리**: 가중치 라우팅, 재시도/타임아웃/서킷브레이커, 미러링
- **보안**: mTLS (자동 인증서 순환), 인증/인가 (RBAC/JWT)
- **관찰성**: 메트릭/로그/트레이스 자동 수집

## Istio vs Linkerd
| | Istio | Linkerd |
|--|-------|---------|
| 프록시 | Envoy (C++) | Linkerd2-proxy (Rust) |
| 리소스 | 높음 | 낮음 |
| 기능 | 풍부 | 핵심 중심 |

## 소스에서
- Netflix: Kueue + 서비스 메시로 워크로드 격리/공정 공유
- Databricks: Pantheon 다중 테넌시 라우팅 (Thanos 라우터)
