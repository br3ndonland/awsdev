# AWS Developer Associate: Cloud Development Kit (CDK)

## Table of Contents <!-- omit in toc -->

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 10.41.40

### CDK definition

- **The [Cloud Development Kit (CDK)](https://docs.aws.amazon.com/cdk/latest/guide/home.html) is a CloudFormation transpiler.** It takes in source code written in other languages, and outputs CloudFormation templates.
- **CDK vs. SDK**
  - Both can provision resources.
  - CDKs transpile (AWS CDK transpiles other code languages to CloudFormation)
  - SDKs are written and used with the same the code language (Boto3 is written in Python)

### CDK languages

- TypeScript (first language supported, many resources available)
- JavaScript (Node.js)
- Python
- Java
- C# (.NET)

### Imperative vs Declarative

- Imperative infrastructure
  - More flexible
  - Less certain
  - Write less code
  - **CDK is imperative**
- Declarative infrastructure
  - Less flexible
  - Very certain
  - Write more code
  - **CloudFormation is declarative**
