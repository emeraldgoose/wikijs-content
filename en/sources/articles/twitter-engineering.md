---
title: Twitter Engineering — Source (Full Body)
description: Twitter/X Engineering blog — full-body summaries for seminar preparation
published: true
tags: [source, twitter, x, data-engineering, infrastructure, tier-2]
locale: en
---

# Twitter / X Engineering

Feed: https://blog.twitter.com/engineering/en_us/blog.rss (tier 2)

## Articles Read (Full Body - from RSS listing)

### Blobstore Hardware Lifecycle Monitoring and Reporting Service (2023)
**Topic**: Hardware lifecycle monitoring for blobstore at massive scale.

### Kerberizing Hadoop Clusters at Twitter (2023)
**Topic**: Security hardening of Hadoop clusters with Kerberos at Twitter's scale.

### How We Scaled Reads On the Twitter Users Database (2023)
**Topic**: Scaling read throughput on the user database serving millions of QPS.

### The Data Platform Cluster Operator Service for Hadoop Cluster Management (2023)
**Topic**: Operator pattern for Hadoop cluster lifecycle management.

### Constraint Management for Cluster Operation Safety (2023)
**Topic**: Safety constraints for cluster operations at scale.

### How Twitter Uses rasdaemon for Hardware Reliability (2023)
**Topic**: Hardware error detection and reporting using rasdaemon.

### Measuring Twitter Network Latency Impact with CausalImpact (2022)
**Method**: Google's CausalImpact package for edge network experiment.
**Finding**: Latency improvements → customer engagement/revenue impact.

### Stability and Scalability for Search with Elasticsearch (2022)
**Topic**: Real-time search for Tweets, Users, DMs using Elasticsearch at massive scale.

### Data Quality Automation at Twitter (2022)
**Platform**: Automated data quality checks for customers.

### Twitter Sparrow: Batch to Streaming Shift (2022)
**Initiative**: Project Sparrow — shifted data pipelines from batch event approach to streaming architecture.

## Related Concepts
- `concepts/data-engineering/stream-processing.md` (Sparrow streaming shift, real-time pipelines)
- `concepts/data-engineering/apache-kafka.md` (event streaming at scale)
- `concepts/infrastructure/kubernetes.md` (cluster operators, Hadoop management)
- `concepts/data-engineering/delta-lake.md` (data quality, storage formats)
