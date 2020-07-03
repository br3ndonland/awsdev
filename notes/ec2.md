# AWS Developer Associate: EC2

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [Intro](#intro)
  - [Instance types](#instance-types)
  - [Placement groups](#placement-groups)
  - [Instance profiles](#instance-profiles)
  - [User data and metadata](#user-data-and-metadata)

## freeCodeCamp ExamPro walkthrough

### Intro

[Video 1](https://youtu.be/RrKRN9zRBWs) 6.59.25

- **EC2 = Elastic Cloud Compute**
- An EC2 instance is the basic unit of AWS infrastructure. Basically all of the other AWS services use EC2 under the hood.

### Instance types

- **General purpose**
  - Balanced compute, memory and networking resources
  - _Use cases:_ web servers, code repos
  - _Instance codes:_ A1, M4, M5, M5a, T2, T3, T3a
- **Compute optimized**
  - High-performance processors
  - _Use cases:_ scientific modeling, gaming servers, ad server engines
  - _Instance codes:_ C4, C5, C5n
- **Memory optimized**
  - For workloads that process large datasets in memory
  - _Use cases:_ in-memory caches and databases, real-time analytics
  - _Instance codes:_ R5, R5a, X1e, X1, z1d, High Memory
- **Accelerated optimized**
  - Hardware co-processors
  - _Use cases:_ machine learning, speech recognition, computational finance
  - _Instance codes:_ F1, G3, P2, P3
- **Storage optimized**
  - High read and write access to large data sets
  - _Use cases:_ NoSQL and relational databases
  - _Instance codes:_ D2, H1, I3, I3en

### Placement groups

- Cluster: instances clustered close together inside a single availability zone (AZ)
- Partition: distributes clusters of instances across separate racks
- Spread: each instance is on a separate rack, and can be in a separate AZs.

### Instance profiles

- **IAM Policy -> IAM Role -> Instance Profile -> EC2 instance**
- **Always avoid embedding your credentials in source code.**
- An **Instance Profile** holds a reference to a role. This allows the EC2 instance to access other AWS services, without needing your direct credentials.

### User data and metadata

- **User data** or `UserData` is a script that is run when an EC2 instance is launched.
- **Meta data** about the instance can be seen at runtime by hitting a URL endpoint: `http://169.254.169.254/latest/meta-data`.
