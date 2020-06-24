# AWS Developer Associate: Cognito

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 4.14.30

- Cognito is decentralized managed authentication
- sign-up/sign-in integration for apps
- **Web identity federation**:
  - Applications federate with identity providers (**IdPs**)
  - Facebook or Google can be IdPs, and Cognito User Pools can be IdPs
  - OIDC uses OAuth
  - SAML is used for single-sign on (SSO)
- **User pools**
  - The user pool is the user's email and password
  - AWS Cognito brokers between AWS and the IdPs
  - Can choose password requirements, user login features (email, phone, etc), and can enable MFA
  - Authentication generates JWT
- **Identity pools**
  - Identity pools exchange the user's authentication JWT for temporary AWS credentials, allowing their application to access other AWS resources like DynamoDB or S3.
- **Cognito sync**
  - Sync user data and preferences across devices with one line of code
