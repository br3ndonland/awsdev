# AWS Developer Associate: VPC

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [Intro](#intro)
  - [Policies](#policies)
  - [Security Token Service (STS)](#security-token-service-sts)

## freeCodeCamp ExamPro walkthrough

### Intro

[Video 1](https://youtu.be/RrKRN9zRBWs) 8.35.00

- **IAM = Identity and Access Management**. Management of users and resources.
- **User**: end users who interact with AWS resources
- **Group**: collections of users with similar permission levels for the entire group
- **Role**: permissions for accessing AWS resources. Cross-account roles allow a user in one account to grant roles to a user in another account.
- **Policy**: JSON documents that grant permissions to users, groups or roles
- See [AWS IAM docs: Security best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)

### Policies

- Managed: managed by AWS, not editable. Orange box icon next to policy name.
- Customer-managed
- Inline: directly attached to user
- Password policies can be set
- Access keys allow users to access AWS through the CLI
- Identity federation allows users to exist on a different platform. These identities are usually built on OAuth2 or Active Directory.

### Security Token Service (STS)

- Allows administrators to create temporary security credentials.
- Roles include `AssumeRoleWithWebIdentity`.
- **Exam question**: order of authentication with `AssumeRoleWithWebIdentity`?
  - First obtain JWT from OAuth2 provider (Google, Facebook, etc)
  - Provider returns JWT
  - Developer calls STS `AssumeRoleWithWebIdentity` with the AWS CLI.
  - AWS STS provisions access key and secret, with a separate `SessionToken` and expiration
