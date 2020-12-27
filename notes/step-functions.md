# Step Functions

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [Step Functions definition](#step-functions-definition)
  - [Step Functions use cases](#step-functions-use-cases)
  - [Step Functions states](#step-functions-states)
  - [Step Functions follow-along](#step-functions-follow-along)
  - [Step Functions cheat sheet](#step-functions-cheat-sheet)

## freeCodeCamp ExamPro walkthrough

[Video 2](https://youtu.be/eCopK1RoyFM) 2.30.45

### Step Functions definition

- **Step functions** create state machines by running multiple AWS services as steps in workflows.
- Step functions are configured with JSON files.

### Step Functions use cases

- Manage Batch job
- Manage Fargate container
- Transfer or remove data records from DynamoDB

### Step Functions states

- Pass: pass input to output without performing work
- Fail: stops execution of state machine
- Wait: delays state machine for specified time
- Task: single unit of work
- Choice: adds branching logic
- Parallel: parallel branches of execution
- Map: iterate over an array

### Step Functions follow-along

Video 2 2.46.15

- Andrew sets up a state machine that integrates [DynamoDB](ddb.md) and [Lambda](lambda.md).
- Andrew debugs the Lambda function, and adds [AWS X-Ray](xray.md) to trace errors.

### Step Functions cheat sheet

Video 2 3.43.15
