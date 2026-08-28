---
title: Scaling Airbnb's Identity Graph with Unified Knowledge Graph Infrastructure
description: Scaling Airbnb’s identity graph with a unified knowledge graph infrastructure
How Airbnb shifts from PaaS to an internal knowledge graph infrastructure at scale.
By:
Lucen Zhao
,
Shukun Yang
,
Ashish Jain
Knowledge graphs offer a natural and powerful way to represent relationships between entities....
published: true
date: 2026-05-19 17:01:01
tags: Graph Database, Key-Value (KV) Caching, Knowledge Graph Infrastructure, Graph Service
editor: markdown
dateCreated: 2026-08-28T14:58:20.324273
---

# Scaling Airbnb's Identity Graph with Unified Knowledge Graph Infrastructure

> **Level**: Advanced  
> **Source**: [Scaling Airbnb’s identity graph with a unified knowledge graph infrastructure](#)  
> **Last Updated**: 2026-08-28

## Introduction

Scaling Airbnb’s Identity Graph with Unified Knowledge Graph Infrastructure denotes the 2024 engineering initiative wherein Airbnb migrated its user relationship database from a Platform-as-a-Service model to a unified, internally managed knowledge graph platform. This transition addresses the increasing scale and query complexity of the system, ensuring robust performance for critical operations. As a foundational layer for Trust and Safety, the infrastructure facilitates essential capabilities such as user identity resolution and relationship understanding. Key use cases include detecting suspicious activities, identifying linked accounts, and supporting broader security applications. By establishing a paved-path graph data platform, Airbnb aims to streamline development while maintaining the integrity of one of its largest and most complex data products.

## Core Concepts

### Concept 1: Unified Knowledge Graph Infrastructure
Airbnb shifted its strategy to move graph data management from a Platform-as-a-Service (PaaS) model to an internally managed platform.
*   **Internal Paved-Path:** In 2024, Airbnb invested in a new, internally managed graph data platform designed as a "paved-path" for developers.
*   **Scalability Focus:** This infrastructure is built to support the scale and complexity required by large graph data products like the Identity Graph.
*   **Unified Standard:** The goal is to create a unified knowledge graph infrastructure that standardizes how graph data is built and managed across the organization.

### Concept 2: The Airbnb Identity Graph
The Identity Graph is a critical application layer built upon the knowledge graph infrastructure, specifically designed for Trust and Safety operations.
*   **Relationship Mapping:** It captures and models relationships between users, treating entities as vertices and relationships as edges.
*   **Trust and Safety:** The graph supports use cases such as detecting suspicious activities and identifying linked accounts to maintain platform security.
*   **Identity Resolution:** It provides aggregated insights that enable the system to understand user identities and their connections accurately.
*   **Complexity and Scale:** The system is recognized as one of Airbnb’s largest and most complex graph data products regarding both volume and query complexity.

### Concept 3: Graph Data Storage Architecture
The underlying storage layer is designed to handle high-volume ingestion and low-latency access through a dual-component system.
*   **Dual-Layer Storage:** The storage consists of a graph database coupled with a key–value (KV) caching layer to optimize performance.
*   **Data Modeling:** Data is structured using a graph model where users represent vertices and relationships represent edges.
*   **Near Real-Time Ingestion:** Most data is ingested asynchronously through events to ensure freshness.
*   **Low-Latency Serving:** The architecture supports real-time service calls that require minimal delay.

### Concept 4: Graph Service Layer
A dedicated service layer acts as the interface between the external applications and the underlying graph storage and logic.
*   **Unified Interface:** The service provides a single, unified interface for all applications to access graph data.
*   **Data Retrieval & Aggregation:** It retrieves data from underlying sources (such as the graph database) and applies necessary aggregation logic.
*   **Model Integration:** The service is capable of applying machine learning models or other logic as needed before serving the data.
*   **Serving Capability:** (Based on available text) The primary function is to serve processed data efficiently to support real-time queries.

## Practical Examples

*No code examples in source article.*

## Related Topics

- [[Distributed Systems]]
- [[Fraud Detection]]
- [[Real-time Data Ingestion]]
- [[Scalability Engineering]]
- [[Data Modeling]]
- [[Platform Engineering]]

## References

- Original Article: [Scaling Airbnb’s identity graph with a unified knowledge graph infrastructure](#)
- Published: 2026-05-19 17:01:01

---

*This page was automatically generated by the Knowledge Base Agent.*
