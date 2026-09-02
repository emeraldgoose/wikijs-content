---
title: Docker — 개념 (번역)
description: en/concepts/infrastructure/docker.md 한국어 번역 요약
published: true
tags: [concept, infrastructure, docker, ko]
locale: ko
---

# Docker — 핵심 요약

## 핵심
- **이미지**: 레이어 스택 (UnionFS), 불변, 재현 가능
- **컨테이너**: 이미지의 실행 인스턴스 (RW 레이어 추가)
- **Dockerfile**: 빌드 명령어 (FROM, RUN, COPY, CMD/ENTRYPOINT)

## 빌드 최적화
- **레이어 캐시**: 변경 적은 것 먼저 (FROM → 시스템 패키지 → 앱 의존성 → 소스)
- **멀티스테이지**: 빌드/런타임 분리 → 최종 이미지 작게
- **.dockerignore**: 불필요한 파일 제외

## 보안
- Non-root USER
- `COPY --chown`
- Read-only rootfs
- Distroless/Alpine 베이스

## 소스에서
- Netflix: Titus (메소스→K8s), Kueue 워크로드 격리
- Uber: 소프트웨어 팩토리 컨테이너화
- Databricks: Pantheon 160 Thanos 인스턴스 K8s 배포
