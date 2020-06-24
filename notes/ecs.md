# AWS Developer Associate: ECS and Fargate

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 2.17.00

ECS: Elastic Container Service

### ECS

- ECS runs Docker containers on EC2 instances
- ECS confusingly calls its container groups “containers.”
- **Tasks** launch containers defined in _taskdef.json_.
- **Services** run tasks.
- **Security groups can be applied to tasks** (may be an exam question).
- The instructor Andrew ran into issues creating the ECS service, even though he is an AWS expert. I think it was partially because he had a `:latest` tag on the end of the service name. He usually tweets at AWS to get them to improve features.

### Fargate

- 2.37.20
- Fargate is serverless (no EC2 or ECS “containers”)
- 2.40.00 Fargate vs Lambda:
  - Fargate offers more customization, but less integration
  - Lambda offers less memory and time, but better integration with other services
- 2.42.45 Fargate follow-along
