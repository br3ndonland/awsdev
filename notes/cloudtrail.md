# AWS Developer Associate: CloudTrail

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [Intro](#intro)
  - [Categories of events trailed by CloudTrail](#categories-of-events-trailed-by-cloudtrail)
  - [Trail options](#trail-options)
  - [Types of events](#types-of-events)
  - [CloudTrail integrations](#cloudtrail-integrations)
  - [Follow-along](#follow-along)

## freeCodeCamp ExamPro walkthrough

### Intro

[Video 1](https://youtu.be/RrKRN9zRBWs) 9.21.45

- **CloudTrail** logs API calls among AWS services.
- CloudTrail enables:
  - Governance
  - Compliance
  - Operational auditing
  - Risk auditing
- By default, CloudTrail collects 90 days of logs via "event history"

### Categories of events trailed by CloudTrail

- Who: `User`, `UserAgent`
- What: region, resource, action
- When: `EventTime`
- Where: source IP address

### Trail options

- Apply trail to all regions
- Apply trail to all accounts in an organization
- Encrypt logs using Server Side Encryption via Key Management Service (SSE-KMS)
- Enable log file validation to ensure logs haven't been tampered with

### Types of events

- Management: operations trailed by default
  - Configuring security (see [iam](iam.md))
  - Registering devices (creating a default [vpc](vpc.md))
  - Configuring rules for routing (creating a subnet in a [vpc](vpc.md))
  - Setting up logging (`CreateTrail`)
- Data: specific operations for AWS services, disabled by default because they are typically high-volume operations.
  - S3 (`GetObject`, `PutObject`, `DeleteObject`, etc)
  - Lambda

### CloudTrail integrations

- CloudTrail can deliver events to CloudWatch logs (but not the other way around)
- CloudTrail logs can be analyzed with Athena

### Follow-along

Video 1 9.27.00
