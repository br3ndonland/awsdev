# AWS Developer Associate: CodeBuild

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [Preface: Intro to Docker](#preface-intro-to-docker)
  - [CodeBuild definition](#codebuild-definition)
  - [Build specification files](#build-specification-files)

## freeCodeCamp ExamPro walkthrough

### Preface: Intro to Docker

[Video 1](https://youtu.be/RrKRN9zRBWs) 11.02.20

I already have experience with Docker, so I breezed through this section.

### CodeBuild definition

[Video 1](https://youtu.be/RrKRN9zRBWs) 11.10.20

- **[CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html)** is a managed build service.
- Eliminates the need to manage build servers (which can be difficult to do)
- Offers pre-packaged build environments for popular programming languages
- Scales automatically
- CodeBuild workflows are specified in source code with _buildspec.yaml_ files.
- Build environments use Docker. There are AWS-managed images, or you can also use your own images.

### Build specification files

- The _buildspec.yaml_ file must be at root of repository
- The version number affects the build environment:
  - 0.1 runs each build command in a separate instance
  - 0.2 runs all build commands in the same instance (recommended)
- Build steps are specified under the `phases` key _(potential exam question)_
- [Buildspec anatomy](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html):

  ```yaml
  version: 0.2

  run-as: Linux-user-name

  env:
    shell: shell-tag
    variables:
      key: "value"
      key: "value"
    parameter-store:
      key: "value"
      key: "value"
    exported-variables:
      - variable
      - variable
    secrets-manager:
      key: secret-id:json-key:version-stage:version-id
    git-credential-helper: no | yes

  proxy:
    upload-artifacts: no | yes
    logs: no | yes

  phases:
    install:
      run-as: Linux-user-name
      runtime-versions:
        runtime: version
        runtime: version
      commands:
        - command
        - command
      finally:
        - command
        - command
    pre_build:
      run-as: Linux-user-name
      commands:
        - command
        - command
      finally:
        - command
        - command
    build:
      run-as: Linux-user-name
      commands:
        - command
        - command
      finally:
        - command
        - command
    post_build:
      run-as: Linux-user-name
      commands:
        - command
        - command
      finally:
        - command
        - command
  reports:
    report-group-name-or-arn:
      files:
        - location
        - location
      base-directory: location
      discard-paths: no | yes
      file-format: JunitXml | NunitXml | CucumberJson | VisualStudioTrx | TestNGXml
  artifacts:
    files:
      - location
      - location
    name: artifact-name
    discard-paths: no | yes
    base-directory: location
    secondary-artifacts:
      artifactIdentifier:
        files:
          - location
          - location
        name: secondary-artifact-name
        discard-paths: no | yes
        base-directory: location
      artifactIdentifier:
        files:
          - location
          - location
        discard-paths: no | yes
        base-directory: location
  cache:
    paths:
      - path
      - path

  ```
