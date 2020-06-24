# AWS Developer Associate: SQS

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 4.34.30

SQS: Simple Queue Service

- **SQS is for application integration.** SQS uses queuing.
- **Queuing**:
  - Simple communication
  - SQS is pull based, not push based.
  - Not real-time
  - Not reactive
  - Examples: SQS, RabbitMQ, Sidekiq
- **Streaming**:
  - Reactive: multiple consumers can react to events/messages
  - Real-time
  - Events live in the stream for longer, so complex operations can be applied
  - Examples: Kinesis, Apache Kafka, NATS
- It's obviously not as black and white as queuing vs streaming in real life
- Use case: mobile app syncing with a desktop app
- Limits
  - Size: messages can only be 1 byte - 256 kb. Amazon SQS extended client library for Java can increase the size to 2 GB because it stores messages in S3.
  - Message retention: 60 seconds - 14 days (default 4 days)
  - Ordering: can do FIFO (first in first out), but it's limited to 300 messages/second
  - Visibility timeout: timeout can be 0 seconds - 12 hours (30 seconds by default) _(may be on exam)_
- Short vs long polling
  - SQS uses short by default
  - Long polling suits the majority of use cases. waits until messages arrive in the queue.
