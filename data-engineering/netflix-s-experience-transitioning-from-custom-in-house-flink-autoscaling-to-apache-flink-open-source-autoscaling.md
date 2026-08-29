---
title: Netflix's experience transitioning from custom in-house Flink autoscaling to Apache Flink open-source autoscaling
description: A Tale of Two Flink Autoscalers
Samuel Yeboah
,
Francesco Di Chiara
and
Mingliang Liu
Today, Netflix runs two Flink autoscalers. That is exactly one more than we want. We built the first one in-house 
published: true
date: 2026-08-21T16:01:01.000Z
tags:
  - Apache Flink
  - AWS
  - Kafka
  - Netflix Data Mesh
editor: markdown
dateCreated: 2026-08-28T23:54:15.000Z
---

# Netflix's experience transitioning from custom in-house Flink autoscaling to Apache Flink open-source autoscaling

> **Level**: Advanced  
> **Source**: [A Tale of Two Flink Autoscalers](#)  
> **Last Updated**: 2026-08-28

## Introduction

Netflix's transition from a proprietary in-house Flink autoscaler to the Apache Flink open-source autoscaler defines a strategic infrastructure modernization for the company's stream processing platform. This migration addresses the prohibitive costs of maintaining custom infrastructure and resolves inefficiencies in peak resource provisioning at massive scale. Key use cases include personalization, advertising, and live event processing across a fleet of over 30,000 Flink jobs managed via the Data Mesh platform. While both systems currently operate in production, Netflix aims to converge on the community solution to reduce technical debt and leverage external innovations.

## Core Concepts

### Concept 1: The Non-Optional Nature of Autoscaling at Massive Scale
Netflix's infrastructure operates at a volume where manual configuration or static provisioning is untenable. The core challenge lies in balancing resource utilization with performance reliability across tens of thousands of jobs.
*   **Volume and Variability:** Netflix operates over 30,000 Flink jobs across multiple AWS regions, with load that fluctuates due to daily cycles, product launches, and regional failovers.
*   **The Provisioning Trade-off:**
    *   **Provisioning for Peak:** Ensures performance but results in significant resource wastage during idle periods.
    *   **Provisioning for Average:** Saves cost but causes latency (lag) during traffic surges.
*   **The Cost of Scaling Actions:** Scaling is not instantaneous or free. For large stateful jobs, a scale operation typically requires taking a savepoint, stopping the job gracefully, and restarting it at a new size—a process that can take minutes and impacts availability.

### Concept 2: The Limitations of In-House ("External") Autóscales
The first autoscaler was built internally around 2019 because mature community options did not exist at the time. While it served early needs, it possessed inherent architectural and capability limitations.
*   **"Watching from Outside":** The custom autoscaler operated externally to the Flink clusters, monitoring metrics rather than being integrated into the JobManager.
*   **Workload Constraints:** It was designed for simpler jobs and could not effectively handle complex stateful pipelines involving branches, joins, or terabytes of state.
*   **Maintainability:** Running a custom solution requires ongoing internal engineering effort to maintain, update, and debug, adding to the infrastructure debt.

### Concept 3: The Advantages of Apache Flink Open-Source Autoscaling
The second autoscaler adopted from the Apache Flink community addresses the gaps left by the custom solution, representing a shift toward standardization.
*   **Broader Capability:** The open-source autoscaler is designed to scale workloads that the homegrown system was never intended for, specifically complex, high-state jobs.
*   **Community Maturity:** By adopting an open-source standard, Netflix leverages community-driven improvements and stability rather than relying solely on internal R&D.
*   **Integration:** It aligns better with the native Flink ecosystem, reducing friction in supporting diverse job types created by the company's Data Mesh platform.

### Concept 4: Strategic Convergence and Infrastructure Debt Management
Netflix is currently in a transitional phase, managing both systems while moving toward a unified stack to minimize operational complexity.
*   **Dual Production State:** As of the report, Netflix runs both the custom and open-source autoscalers in production, which is described as "exactly one more than we want."
*   **Convergence Goal:** The strategy is to steadily converge on the open-source autoscaler to eliminate the custom code and consolidate operations.
*   **Core Lesson:** The experience highlights the "real price" of maintaining custom infrastructure. It emphasizes evaluating whether a problem can be solved by adopting a mature community tool rather than building and maintaining a specialized internal system.

## Practical Examples

*No code examples in source article.*

## Related Topics

- [[Cloud Cost Optimization]]
- [[Distributed Systems Architecture]]
- [[Site Reliability Engineering (SRE)]]
- [[Open Source Adoption Strategy]]
- [[Stream Processing Infrastructure]]

## References

- Original Article: [A Tale of Two Flink Autoscalers](#)
- Published: 2026-08-21

---

*This page was automatically generated by the Knowledge Base Agent.*
