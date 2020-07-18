# AWS Developer Associate: RDS

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [RDS definition](#rds-definition)
  - [RDS encryption](#rds-encryption)
  - [RDS backups](#rds-backups)
  - [Availability zones and replicas](#availability-zones-and-replicas)
  - [Follow-along](#follow-along)

## freeCodeCamp ExamPro walkthrough

[Video 2](https://youtu.be/eCopK1RoyFM) 0.26.00

### RDS definition

- [RDS](https://docs.aws.amazon.com/rds/) is AWS **Relational Database Service**, a managed service for relational databases.

### RDS encryption

- Encryption at-rest is available for all database engines
- Backups and snapshots can also be encrypted with [KMS](kms.md).

### RDS backups

- There are two options:
  1. Automated backups
  2. Manual snapshots
- To restore from the console: Actions -> Restore to point in time. Will have new endpoint.

### Availability zones and replicas

- Multi-AZ deployment creates a mirror in another zone
- Read-only replicas can increase performance

### Follow-along

Video 2 0.33.00

- Create an RDS Postgres instance
- Create a snapshot
- Create an Aurora instance for MySQL and Postgres
