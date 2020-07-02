# AWS Developer Associate: CloudFormation

## Table of Contents <!-- omit in toc -->


## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 9.35.30

### CloudFormation definition

- **CloudFormation** is a way to declare AWS infrastructure using code. This is known as [infrastructure as code](https://en.wikipedia.org/wiki/Infrastructure_as_code).
- See the [AWS CloudFormation docs: What is CloudFormation?](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)

### Benefits of infrastructure as code

- **Simplify infrastructure management**: when configuring deployments with the browser console, each service has to be configured individually. Infrastructure as code allows configuration of multiple services in one JSON or YAML file.
- **Replicate and reproduce deployments**: configuring deployments with the browser console doesn't scale. What if you need to repeat the configuration once more? Ten more times? Infrastructure as code enables replication (repeating deployments within the same set of cloud resources) and reproduction (repeating deployments with a different cloud organization or set of resources).
- **Track changes to infrastructure**: when configuring deployments with the browser console, it is difficult to keep track of changes made over time after the deployment is initially created. Infrastructure as code allows deployments to be tracked with version control like Git.

