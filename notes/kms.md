# AWS Developer Associate: KMS

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 4.04.30

Key management service

- Integrates with many AWS services, such as S3
- KMS is built on Hardware Security Modules (HSMs):
  - Tamper-proof servers that store keys in-memory only instead of on-disk.
  - HSMs are multi-tenant, and the tenants are isolated virtually.
  - CloudHSM offers a single-tenant HSM for more security.
- CMS: Customer Master Key
  - Primary resources in KMS
- AWS KMS supports symmetric and asymmetric keys
  - Symmetric is a single 256 bit key (encrypting an S3 bucket)
  - Asymmetric keys are RSA key pairs
- **KMS CLI commands** _(potential exam question)_
  - `aws kms create-key`
  - `aws kms encrypt`
  - `aws kms decrypt`
  - `aws kms re-encrypt`
  - `aws kms enable-key-rotation`: only works on symmetric keys
- I noticed a [longstanding bug](https://github.com/aws/aws-cli/issues/2383) with the help commands:

```
~
❯ aws kms help
<string>:18: (WARNING/2) Inline interpreted text or phrase reference start-string without end-string.
```
