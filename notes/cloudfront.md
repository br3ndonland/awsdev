# AWS Developer Associate: CloudFront

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [Intro](#intro)
  - [Distribution](#distribution)
  - [Protection](#protection)
  - [Cache invalidation](#cache-invalidation)
  - [Lambda@Edge Functions](#lambdaedge-functions)
  - [Follow-along](#follow-along)

## freeCodeCamp ExamPro walkthrough

### Intro

[Video 1](https://youtu.be/RrKRN9zRBWs) 9.02.45

- CloudFront is a **Content Delivery Network (CDN)**
- CDNs distribute content among many "edge" servers. When a user requests resources, they are returned from the server closest to the user.

### Distribution

- A **distribution** is a collection of edge locations with a common origin (S3, EC2, ELB, Route53)
- Distributions allow everyone access by default

### Protection

- Help restrict access to certain users
- An **[Origin Access Identity (OAI)](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudfront-cloudfrontoriginaccessidentity.html)** is a virtual user ID that allows them to fetch private resources from a CloudFront Distribution
- There are also **signed cookies** (passed to CloudFront with the request) and **signed URLs**. Note that signed URLs are different from S3 Presigned URLs. ExamPro uses signed cookies for video streaming. Videos stream in parts, so you need a cookie to allow all the parts.

### Cache invalidation

- Resources on CDNs are cached.
- If resources are updated, the cache can be invalidated for faster updates.
- **Time To Live (TTL)** is the time until the cache refreshes.
- **Cache refreshing costs money.** The servers need to transfer new resources, which requires bandwidth.

### Lambda@Edge Functions

Override request and response behavior

1. Viewer request: can be used to only display resources to authenticated users
2. Origin request
3. Origin reponse
4. Viewer reponse

### Follow-along

Video 1 9.11.00
