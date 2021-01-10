# AWS Developer Associate: Cloud Development Kit (CDK)

## Table of Contents <!-- omit in toc -->

- [CDK basics](#cdk-basics)
  - [CDK definition](#cdk-definition)
  - [CDK vs. SDK](#cdk-vs-sdk)
  - [Imperative vs Declarative](#imperative-vs-declarative)
  - [CDK languages](#cdk-languages)
- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)

## CDK basics

### CDK definition

**The [Cloud Development Kit (CDK)](https://docs.aws.amazon.com/cdk/latest/guide/home.html) is a CloudFormation transpiler.** It takes in source code written in other languages, and outputs CloudFormation templates.

There is also a [Terraform CDK (`cdktf`)](https://github.com/hashicorp/terraform-cdk), which is built on the AWS CDK, but transpiles to Terraform instead of CloudFormation.

### CDK vs. SDK

- Both can provision resources.
- CDKs transpile (AWS CDK transpiles other code languages to CloudFormation)
- SDKs are written and used with the same the code language (Boto3 is written in Python). See the [Terraform docs](https://www.terraform.io/intro/vs/boto.html) for a helpful comparison.

### Imperative vs Declarative

- **Imperative** infrastructure _(issuing commands with programming languages)_
  - More flexible
  - Less certain
  - Write less code
  - **The AWS CDK is imperative.**
- **Declarative** infrastructure _(making statements about infrastructure without specifying the exact commands)_
  - Less flexible
  - Very certain
  - Write more code
  - **CloudFormation is declarative.**

### CDK languages

- TypeScript (first language supported, many resources available)
- JavaScript (Node.js)
- Python
- Java
- C# (.NET)

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 10.41.40
