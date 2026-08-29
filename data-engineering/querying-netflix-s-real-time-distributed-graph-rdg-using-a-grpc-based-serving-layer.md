---
title: Querying Netflix's Real-Time Distributed Graph (RDG) using a gRPC-based serving layer
description: How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…
How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC execution
published: true
date: 2026-08-07T16:01:02.000Z
tags:
  - gRPC
  - Apache Flink
  - Real-Time Distributed Graph (RDG)
editor: markdown
dateCreated: 2026-08-28T23:38:48.000Z
---

# Querying Netflix's Real-Time Distributed Graph (RDG) using a gRPC-based serving layer

> **Level**: Advanced  
> **Source**: [How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…](#)  
> **Last Updated**: 2026-08-28

## Introduction

Netflix's gRPC-based serving layer is a specialized execution API engineered to facilitate low-latency querying of the company's Real-Time Distributed Graph (RDG). This infrastructure is essential for validating the data pipeline, as ingestion and storage capabilities are rendered ineffective without the ability to rapidly retrieve complex graph patterns at scale. Designed to manage billions of nodes and edges while enforcing single-digit-millisecond latency requirements, the serving layer empowers internal engineering partners to access real-time insights for decision-making and system optimization. By leveraging the gRPC protocol, the architecture delivers a flexible and scalable interface that bridges massive distributed storage with the immediate execution of dynamic graph traversal logic. Consequently, it transforms raw graph data into actionable intelligence, ensuring that the RDG functions as a responsive resource for critical business operations.

## Core Concepts

### High-Performance Transport via gRPC and Protobuf
Netflix selected gRPC as the core transport layer for the RDG serving layer to overcome the latency and overhead limitations of traditional REST/JSON APIs.
*   **Binary Serialization:** Utilizing Protocol Buffers (Protobuf) instead of JSON significantly reduces payload size and serialization/deserialization time, which is critical for achieving sub-100ms response times.
*   **HTTP/2 Multiplexing:** gRPC leverages HTTP/2 to allow multiple queries to be sent over a single TCP connection simultaneously, reducing connection overhead and improving throughput under high load.
*   **Strong Typing:** The use of `.proto` files for API contracts ensures type safety between the client and server, reducing runtime errors and facilitating easier schema evolution.

### The Java Client SDK Abstraction
To simplify adoption for internal partners and hide the complexity of the underlying distributed system, Netflix built a high-level Java SDK.
*   **Encapsulation:** The SDK abstracts away raw gRPC calls, connection pooling, and SSL/TLS handshake management, allowing developers to interact with the graph using simple method calls.
*   **Built-in Resilience:** It handles common distributed system challenges such as automatic retries, circuit breaking, and connection health checks without requiring client-side code.
*   **Metrics Integration:** The SDK is instrumented to automatically emit observability data (latency histograms, error counts) to Netflix's monitoring systems (Atlas), ensuring visibility into query performance.

### Distributed Query Coordination
The serving layer uses a coordinator-worker architecture to manage the complexity of querying a sharded graph stored across many nodes.
*   **Query Planning:** A central coordinator receives the query request, determines which storage shards hold the relevant data, and formulates a parallel execution plan.
*   **Shard Dispatch:** The coordinator dispatches sub-queries to the specific worker nodes where the graph data resides, allowing for parallel execution across the cluster.
*   **Result Aggregation:** Once the workers return their partial results, the coordinator merges, sorts, and filters the data before sending the final response back to the client.

### Query Safety and Resource Guardrails
To prevent complex graph traversals from overwhelming the system or causing denial-of-service scenarios, strict execution limits are enforced at the serving layer.
*   **Traversal Limits:** Queries are restricted by maximum depth (how many hops deep) and maximum edge count (how many relationships can be traversed) to prevent exponential explosion of data processing.
*   **Timeouts:** Every query has a hard timeout budget (e.g., 50ms) to ensure that long-running exploratory queries do not impact latency for high-priority security checks.
*   **Cost Budgeting:** The system assigns a "cost" to different types of operations, allowing the serving layer to reject queries that exceed the allocated resource budget for a specific user or API key.

### Cursor-Based Pagination
To handle deep exploratory workloads like personalization traces, the API supports efficient iteration over large result sets without memory overload.
*   **Skip/Offset Avoidance:** Instead of using traditional offset-based pagination (which becomes slow on large datasets), the API uses cursor-based pagination.
*   **Stateful Iteration:** Clients receive a token (cursor) in the response that represents the current position in the result set, allowing them to fetch the next page efficiently from any shard.
*   **Memory Efficiency:** This ensures that no query ever requires loading the entire result set into memory simultaneously, maintaining consistent latency regardless of the result size.

## Practical Examples

*No code examples in source article.*

## Related Topics

- [[Graph Databases]]
- [[Distributed Systems Architecture]]
- [[Low Latency API Design]]
- [[Stream Processing]]
- [[System Scalability]]

## References

- Original Article: [How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…](#)
- Published: 2026-08-07

---

*This page was automatically generated by the Knowledge Base Agent.*
