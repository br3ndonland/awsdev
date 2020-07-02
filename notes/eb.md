# AWS Developer Associate: Elastic Beanstalk

Elastic Beanstalk is like Heroku on AWS

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) beginning

### Environments

- Frequently have web and worker environments.
  - Web for main application
  - Worker for background jobs
- _Why do you need an ELB (Elastic Load Balancer) if you have an AutoScaling Group (ASG)?_

### Deploys

- **All-at-once**
- **Rolling** updates will have downtime and reduced capacity. Require ELB, so cannot be used with single-instance web environments.
- **Rolling with additional batch** adds servers during the update so you never have reduced capacity. In case of failure, you may need an additional update to roll back the changes.
- **Immutable** relies on an ASG. The entire ASG is deployed as a batch. The easiest and safest way to deploy. In case of failure, you just terminate the new ASG.
- **Blue/Green** deployments are similar to immutable, but have a DNS change because they point to a new load balancer. DNS changes take time to propagate.
- The definition of _in-place_ varies with scope: _(potential exam question)_
  - **The exams use in-place to refer to the scope of the elastic beanstalk environment.** All-at-once, rolling, rolling with additional batch, and immutable are considered in-place.
  - If in-place refers to the scope of a single server, only all-at-once or rolling would be considered in-place.
  - If scope is an uninterrupted server, you need to do a zero-downtime deploy. EB can’t do this. Classic way to do this: Ruby on Rails + Unicorn + Capistrano
- In-place vs blue/green
  - If we use the EB environment as the boundary for in-place, then for immutable deploys, the ELB can seamlessly switch to a new ASG.
  - Blue and green can be separate environments, so the ELB can’t seamlessly switch over. There can be downtime.
  - _Why would you use blue/green?_ -> If your database needs to persist. The database is outside the EB env, probably in RDS. With immutable deploys, the database has to be within the EB environment, and it gets destroyed when switching to a new environment.

### Repo configuration

- [Config files](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html) in _/.ebextensions_ with extension _.config_
- _env.yml_ is the **environment manifest**
  - `EnvironmentName`: add a `+` to use environment groups
  - `SolutionStack` determines which Amazon Machine Image (AMI) is chosen

### Server configuration

- Also in _env.yml_?
- You can provide custom images to improve provisioning times
- _dockerrun.aws.json_ can be used to specify [multi-container configuration](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_docker_ecs.html). _TODO: why not docker-compose.yml?_

### CLI

- Heroku-like experience
- Seems to provide a little more than the standard AWS CLI

### Follow-along

- Video 1 0.59.00
- 1.36.00 IAM troubleshooting: didn’t create the proper service role, particle because the project was created from the command line in Cloud9. Don’t manually create it, try creating through the web UI or just re-do `eb create` in Cloud9.
- 1.46.00 Changing to`DeploymentPolicy: Immutable` in a _.config_ file. Note that the instructor typed a key incorrectly: `IngoreHealthCheck`.
- Blue/green: use `eb swap`
- 1.58.00 Docker container
- 2.01.30 [Single Docker container with ECR](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/single-container-docker-configuration.html):
  - Have to create a repo in ECR first
  - Also have to give EB permission to access ECR (attach permissions to EB role)
  - AWS CLI with `aws ecr`. Need to use a Docker credential helper to avoid committing credentials
