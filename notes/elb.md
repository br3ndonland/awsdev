# AWS Developer Associate: ELB

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [Intro](#intro)
  - [Rules of traffic](#rules-of-traffic)
  - [Other details](#other-details)

## freeCodeCamp ExamPro walkthrough

### Intro

[Video 1](https://youtu.be/RrKRN9zRBWs) 7.36.00

- **ELB = Elastic Load Balancer**
- Three ELBs available:
  1. Application Load Balancer (ALB) (HTTP/HTTPS)
  2. Network Load Balancer (NLB) (TCP/UDP, useful for high network throughput, video games for example)
  3. Classic Load Balancer (CLB) (legacy, no rules available)

### Rules of traffic

- Listeners: listen for incoming traffic
- Rules: rules determine what to do with traffic
- Target groups: traffic directed to EC2 instances

### Other details

- `X-Forwarded-For` (XFF) identifies the originating IP address of a client connecting to a web server through a proxy (like a load balancer)
- Health checks can redirect traffic from unhealthy instances to healthy instances.
- NLB and CLB have cross-zone load balancing available.
- Request routing: can be useful for applications with different environments (production, development, staging, etc). Note the `X-ENV=production` header.
