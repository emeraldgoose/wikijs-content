---
type: concept
concept_id: con_756833888c69
canonical_name: How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…
slug: how-and-why-netflix-built-a-real-time-distributed-graph-part-3-querying-the-graph-with-grpc
status: active
confidence: 0.9
category: data-engineering
concept_type: concept
created_at: 2026-08-29 05:49:54.360926
updated_at: 2026-08-29 05:49:54.360929
---

# How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…

## Overview

title: How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…

## Definition

- Part 1 of the series described using Apache Flink to build an ingestion and processing pipeline that turns streaming events into graph primitives. 🟢
- This article is the third entry of a multi-part blog series describing how Netflix built a Real-Time Distributed Graph (RDG). 🟢
- Model Scoring Service (MSS) is the shared inference backend supporting XGBoost, TensorFlow, PyTorch, and LLMs 🟢

## Features

- Part 2 of the series discussed designing a storage layer to handle billions of nodes and edges while maintaining single-digit-millisecond latency. 🟢
- NVIDIA Triton Inference Server manages model loading, batching, and GPU scheduling underneath MSS 🟢
- Member-scale ML at Netflix is fronted by a unified JVM-based serving system 🟢
- The serving layer is designed to turn a constantly evolving, billion-edge graph into sub-100ms responses. 🟢
- Small CPU models run in-process to avoid remote-call overhead 🟢

## Usage

- Netflix runs the full LLM stack internally from model deployment through inference instead of using hosted APIs 🟢
- Netflix needed to handle access patterns ranging from high-volume security lookups to deep, exploratory personalization traces. 🟢

## Sources

1. [How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…](https://netflixtechblog.com/how-and-why-netflix-built-a-real-time-distributed-graph-part-3-querying-the-graph-with-grpc-0f3468349607?source=rss----2615bd06b42e---4) - Netflix Technology Blog
2. [In-House LLM Serving at Netflix](https://netflixtechblog.com/in-house-llm-serving-at-netflix-a5a8e799ea2c?source=rss----2615bd06b42e---4) - Netflix Technology Blog
3. [How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…](https://netflixtechblog.com/how-and-why-netflix-built-a-real-time-distributed-graph-part-3-querying-the-graph-with-grpc-0f3468349607?source=rss-c3aeaf49d8a4------2)

## Evidence

Detailed evidence with source attribution:

### Part 1 of the series described using Apache Flink to build an ingestion and processing pipeline that turns streaming events into graph primitives.

**Source**: [How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…](https://netflixtechblog.com/how-and-why-netflix-built-a-real-time-distributed-graph-part-3-querying-the-graph-with-grpc-0f3468349607?source=rss----2615bd06b42e---4)
**Location**: Introduction paragraph 1
**Confidence**: 1.00

---

### Part 2 of the series discussed designing a storage layer to handle billions of nodes and edges while maintaining single-digit-millisecond latency.

**Source**: [How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…](https://netflixtechblog.com/how-and-why-netflix-built-a-real-time-distributed-graph-part-3-querying-the-graph-with-grpc-0f3468349607?source=rss----2615bd06b42e---4)
**Location**: Introduction paragraph 1
**Confidence**: 1.00

---

### This article is the third entry of a multi-part blog series describing how Netflix built a Real-Time Distributed Graph (RDG).

**Source**: [How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…](https://netflixtechblog.com/how-and-why-netflix-built-a-real-time-distributed-graph-part-3-querying-the-graph-with-grpc-0f3468349607?source=rss----2615bd06b42e---4)
**Location**: Introduction paragraph 1
**Confidence**: 1.00

---

### NVIDIA Triton Inference Server manages model loading, batching, and GPU scheduling underneath MSS

**Source**: [In-House LLM Serving at Netflix](https://netflixtechblog.com/in-house-llm-serving-at-netflix-a5a8e799ea2c?source=rss----2615bd06b42e---4)
**Location**: Architecture Overview
**Confidence**: 0.95

---

### Model Scoring Service (MSS) is the shared inference backend supporting XGBoost, TensorFlow, PyTorch, and LLMs

**Source**: [In-House LLM Serving at Netflix](https://netflixtechblog.com/in-house-llm-serving-at-netflix-a5a8e799ea2c?source=rss----2615bd06b42e---4)
**Location**: Architecture Overview
**Confidence**: 0.95

---

### Member-scale ML at Netflix is fronted by a unified JVM-based serving system

**Source**: [In-House LLM Serving at Netflix](https://netflixtechblog.com/in-house-llm-serving-at-netflix-a5a8e799ea2c?source=rss----2615bd06b42e---4)
**Location**: Architecture Overview
**Confidence**: 0.95

---

### Netflix runs the full LLM stack internally from model deployment through inference instead of using hosted APIs

**Source**: [In-House LLM Serving at Netflix](https://netflixtechblog.com/in-house-llm-serving-at-netflix-a5a8e799ea2c?source=rss----2615bd06b42e---4)
**Location**: Introduction
**Confidence**: 0.95

---

### Netflix needed to handle access patterns ranging from high-volume security lookups to deep, exploratory personalization traces.

**Source**: [How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…](https://netflixtechblog.com/how-and-why-netflix-built-a-real-time-distributed-graph-part-3-querying-the-graph-with-grpc-0f3468349607?source=rss----2615bd06b42e---4)
**Location**: The Real World Needs paragraph 1
**Confidence**: 0.95

---

### The serving layer is designed to turn a constantly evolving, billion-edge graph into sub-100ms responses.

**Source**: [How and Why Netflix Built a Real-Time Distributed Graph: Part 3 — Querying the graph with gRPC…](https://netflixtechblog.com/how-and-why-netflix-built-a-real-time-distributed-graph-part-3-querying-the-graph-with-grpc-0f3468349607?source=rss----2615bd06b42e---4)
**Location**: Introduction paragraph 2
**Confidence**: 0.95

---

### Small CPU models run in-process to avoid remote-call overhead

**Source**: [In-House LLM Serving at Netflix](https://netflixtechblog.com/in-house-llm-serving-at-netflix-a5a8e799ea2c?source=rss----2615bd06b42e---4)
**Location**: Architecture Overview
**Confidence**: 0.90

---

---

*Generated from Knowledge State on 2026-08-30 07:19:04*

*Concept ID: `con_756833888c69`*
