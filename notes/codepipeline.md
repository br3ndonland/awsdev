# AWS Developer Associate: CodePipeline

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [CodePipeline definition](#codepipeline-definition)
  - [CodePipeline stages and transitions](#codepipeline-stages-and-transitions)
- [CodePipeline and GitHub](#codepipeline-and-github)

## freeCodeCamp ExamPro walkthrough

[Video 2](https://youtu.be/eCopK1RoyFM) 0.16.20

### CodePipeline definition

- **CodePipeline** is a fully-managed CI/CD pipeline tool.
- CodePipeline can combine tasks from other services like [CodeCommit](codecommit.md), [CodeBuild](codebuild.md), and [CodeDeploy](codedeploy.md).

### CodePipeline stages and transitions

- **Stages** are steps in the pipeline
- **Stage transitions** link stages together.

## CodePipeline and GitHub

I have worked with CodePipeline in production. The major drawback is that the **integration with GitHub is poor**.

- _GitHub -> AWS CodePipeline:_ GitHub can be configured as a source provider. This will add [webhooks](https://docs.github.com/en/developers/webhooks-and-events/webhooks) to the GitHub repo. Webhooks are not very configurable. They fire in response to general triggers, such as pushes or releases. There's not really a way to only kick off your CodePipeline if your other GitHub checks pass (like [GitHub Actions workflows](https://github.com/features/actions)).
- _AWS CodePipeline -> GitHub:_ CodePipeline doesn't report back to GitHub, nor do they provide a GitHub App like other third-party integrations do. [Travis CI](https://github.com/marketplace/travis-ci) reports status back to GitHub in real-time. The [Azure Pipelines GitHub app](https://github.com/marketplace/azure-pipelines) also integrates well with GitHub. Even other AWS services that do report back to GitHub may be broken when run through CodePipeline. For example, [CodeBuild provides README badges](https://docs.aws.amazon.com/codebuild/latest/userguide/sample-build-badges.html) that show the status of the build job. These tend to work for CodeBuild jobs, but if there's a CodeBuild job run through CodePipeline, the status always shows up as unknown.

If you use GitHub to manage source control, I would suggest using the [GitHub Actions AWS workflows](https://github.com/marketplace?type=actions&query=aws) to trigger AWS services (like CodeBuild, CodeDeploy, and ECS/Fargate) instead of CodePipeline.
