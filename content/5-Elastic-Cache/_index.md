---
title : "ElastiCache"
date : "2025-07-28" 
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

ElastiCache Valkey is used to dramatically improve ML inference performance by caching prediction results. Without caching, each ML inference request takes 300-500ms, but with caching we achieve 50ms response times (90% faster). For our fraud detection use case requiring sub-50ms responses at 10,000 requests/second during peak traffic, caching reduces Lambda compute costs by 70% while ensuring instant responses for repeated predictions. The system checks cache first, returns cached results immediately if found, or runs the ML model and caches the result for future requests, targeting 70%+ cache hit rate for optimal performance.

