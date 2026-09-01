---
title: Agent — 개념 (번역)
description: en/concepts/ai-engineering/agent.md 한국어 번역 요약
published: true
tags: [concept, ai-engineering, agent, ko]
---

# AI Agent — 핵심 요약

## 아키텍처
**Agent = Model + Harness + Memory + Tools**

## System2/System1 (PonderPounce)
| | System2 (Ponder) | System1 (Pounce) |
|--|------------------|------------------|
| 속도 | 느림 (숙고) | 빠름 (반응) |
| 컨텍스트 | 전체 에피소드 | 압축 토큰 |
| 역할 | 서브골, 추론 | 액션 실행 |

## 하네스 (JIT-Agent 4모듈)
1. 메모리 관리
2. 플래닝 전략
3. 액션 프로토콜
4. 도구/스킬 오케스트레이션

## 안전성 (StepGuard)
- 단계별 가드: 실행 전 도구 액션 검사
- 77.3% 공격 감소, 2.8pp 유틸리티 감소
