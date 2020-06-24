# AWS Developer Associate: Secrets Manager

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 4.58.18

- Mostly used to store and rotate database credentials (RDS, Redshift, etc)
- Credentials can auto-rotate using a Lambda function
- Encrypted at rest by KMS
- $0.40 per secret per month, $0.05 per 10K API calls
- CloudTrail can monitor credentials access.
- CLI:
  - `aws secretsmanager get-secret-value`
  - `aws secretsmanager describe-secret`
