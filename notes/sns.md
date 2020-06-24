# AWS Developer Associate: SNS

[Video 1](https://youtu.be/RrKRN9zRBWs) 4.26.40

## freeCodeCamp ExamPro walkthrough

SNS: Simple Notification Service

- **Pub/Sub** is used for application integration
  - Publishers send messages to an event bus
  - Event bus pushes messages out to subscribers
- **Topics** group subscriptions together. Topics can be encrypted with KMS.
- Protocols:
  - HTTP/HTTPs webhooks
  - Email (plain text only, can't use AWS SES)
  - Email-JSON
  - Amazon SQS
  - AWS Lambda
  - SMS
  - Platform application endpoints (push notifications)
