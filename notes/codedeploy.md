# AWS Developer Associate: CodeDeploy

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [CodeDeploy definition](#codedeploy-definition)
  - [In-place vs blue/green deployments](#in-place-vs-bluegreen-deployments)
  - [App specification files](#app-specification-files)
  - [Requirements](#requirements)
  - [Follow-along](#follow-along)
- [CodeDeploy feedback](#codedeploy-feedback)

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 11.19.50

### CodeDeploy definition

- **[CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html)** is a managed Continuous Deployment (CD) platform.
- Integrates with infrastructure as code tools like CloudFormation (see [CodeDeploy docs](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployments-create-ecs-cfn.html) and [CloudFormation docs](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/blue-green.html))
- Integrates with configuration management tools like Ansible, Puppet, and Chef

### In-place vs blue/green deployments

- **In-place deployments**
  - Previous deployment is stopped, then the new deployment is installed (downtime)
  - Only available for EC2 or on-premises deployments
- **Blue/green deployments**
  - New deployment is started before stopping the previous deployment
  - After new deployment is verified, traffic is re-routed from old deployment (no downtime)

Also see the deploys section of my [Elastic Beanstalk notes](eb.md).

### App specification files

- CodeDeploy deployments are specified in _appspec.yaml_ files.
- `version` is currently `0.0`, but is required in case versions are added in the future.
- `resources` declare ECS services used
- [`hooks`](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html) declare lifecycle hooks (events, and what to do at each event).
- Default hooks for ECS:
  - `BeforeInstall`
  - `AfterInstall`
  - `AfterAllowTestTraffic`
  - `BeforeTestTraffic`
  - `AfterTestTraffic`
- EC2 deployments require a few extra fields like `os`, `files`, and `permissions`.
- [Appspec anatomy](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure.html#ecs-appspec-structure):

  ```yaml
  version: 0.0
  resources: ecs-service-specifications
  hooks: deployment-lifecycle-event-mappings
  ```

### Requirements

- CodeDeploy Agent: installed on EC2 instances to allow reporting back to CodeDeploy
- CodeDeploy service role: IAM role to allow CodeDeploy to perform tasks like creating ASGs

### Follow-along

Video 1 11.31.30

- The instructor Andrew creates an EC2 instance, then adds CodeDeploy to it.
- The cheat sheet arrives in Video 2 0.14.30

## CodeDeploy feedback

**I have worked with CodeDeploy in production. CodeDeploy is supposed to improve deployments, but can also make them more difficult.** For example, when performing [blue/green deployments](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/blue-green.html), CodeDeploy steps through a series of [lifecycle hooks](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html), only some of which are configurable. The `Install` hook has an hour timeout and can't be configured, which means that deployments can hang for an hour, or even an entire day, with no additional information about why they didn't work.

In the [CodePipeline notes](./codepipeline.md#codepipeline-and-github), I mentioned that integration between GitHub and CodePipeline is poor. The integration between GitHub and CodeDeploy is a little better, thanks to GitHub's CI/CD service [GitHub Actions](https://docs.github.com/en/free-pro-team@latest/actions). After creating an IAM role for GitHub Actions, I use the [ECS deploy task definition action](https://github.com/marketplace/actions/amazon-ecs-deploy-task-definition-action-for-github-actions) to trigger deployments. It is important to be careful about how the deployment is configured, because of the limitations of lifecycle hooks described above. Hanging lifecycle hooks can waste not only AWS time, but also GitHub Actions build time. For example, if `wait-for-service-stability: true` is set with the [ECS deploy task definition action](https://github.com/marketplace/actions/amazon-ecs-deploy-task-definition-action-for-github-actions) in a GitHub Actions workflow, GitHub has to wait for CodeDeploy and charge for time that CodeDeploy is hanging. To avoid hanging deployments, be sure to add a timeout to your GitHub Actions workflow with `wait-for-minutes: 10`. Ten minutes is usually adequate for a production deployment to complete.
