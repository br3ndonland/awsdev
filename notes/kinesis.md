# AWS Developer Associate: Kinesis

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 4.45.15

- Data streaming service used for real-time communication
  - Stock prices
  - Gaming
  - Social networks
  - Geospacial
  - Click stream data
- Kinesis data streams
  1. Data streams: splits the stream into shards, can have multiple consumers
  2. Data firehose: single consumer (S3, Redshift, Elasticsearch, splunk)
  3. Video streams: ingest video and audio from webcams, security cameras, mobile; output to ML or video processing services (SageMaker, Rekognition)
  4. Data analytics: real-time analytics with SQL
- KPL (Kinesis Producer Library) is a Java library for writing data to a stream
