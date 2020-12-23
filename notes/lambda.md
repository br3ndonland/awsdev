# Lambda

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)

## freeCodeCamp ExamPro walkthrough

[Video 2](https://youtu.be/eCopK1RoyFM) 2.03.00

- **[Serverless](https://aws.amazon.com/serverless/)**: Run code without provisioning or managing servers.
- **[AWS Lambda](https://aws.amazon.com/lambda/)**: AWS serverless platform.
  - Runs code only when requested
  - Scales automatically
  - Charges per invocation
  - Used to connect different services
  - Very versatile
- **AWS Lambda triggers**:
  - Available for many AWS services (DynamoDB, etc)
  - Trigger Lambda functions
- **AWS Lambda pricing**
  - First 1 million requests per month free, $0.20/million requests after that
  - 400,000 GB-seconds per month free, $0.000016667/GB-second after that (may increase if more memory allocated)
  - Account can only have 1000 Lambda functions running concurrently
  - Lambda functions can run for 15 minutes max. Consider Fargate for longer run-times (see [ecs notes](ecs.md)).
  - Memory can be 128-3008 MB, in 64 MB increments
- **Cold starts**
  - Negative trade-off of using serverless
  - There is a delay while servers are starting up
  - Pre-warming can help keep servers running
- **Function versions**
  - Lambda functions can be versioned to manage deployment
  - Lambda functions are referenced with the ARN (Amazon Resource Number)
  - There are unqualified and qualified function versions
  - Unqualified always points to the latest function version
  - Qualified can point to a specific version
- **Lambda aliases**
  - Aliases provide human-readable names for function versions
- **Lambda layers**
  - Zip archives that can be used by Lambda functions
  - Each function can have 5 layers
  - Total size of all layers combined must be <250 MB.
- [AWS SAM](https://aws.amazon.com/serverless/sam/) (Serverless Application Model)
- [Chalice](https://aws.github.io/chalice/index.html) is a Python serverless microframework for AWS. It's like Flask+Boto3+Lambda.
