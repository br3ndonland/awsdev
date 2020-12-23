# ElastiCache

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)

## freeCodeCamp ExamPro walkthrough

[Video 2](https://youtu.be/eCopK1RoyFM) 1.59.00

- **Cache**: In-memory data storage. Temporary storage location for data.
- **Durability**: Risk of losing data. High durability means low risk of losing data.
- **ElastiCache**: AWS implementation of two popular open-source caching engines, Redis and Memcached.
  - **Memcached** is a simple key:value store. Simplicity makes it fast. It is "generally preferred for caching HTML fragments."
  - **Redis** can perform many different kinds of operations, and is also very fast.
  - Don't search for comparisons between Memcached and Redis, "unless you want to read endless arguments as if people are arguing 'Kirk vs Picard'."
- **In order to use ElastiCache, the in-memory data store must be in the same VPC.**
