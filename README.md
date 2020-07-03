# AWS Developer Associate certification

<img src="./notes/img/aws-certifications.png" alt="AWS certifications" width="600px">

## Description

**This repository contains resources from my work on the [AWS Developer Associate certification](https://aws.amazon.com/certification/certified-developer-associate/). It's mostly notes right now, but after I pass the exam, I will add more code examples.**

I created the repository with the [GitHub CLI](https://cli.github.com/):

```sh
~/dev/aws
❯ gh repo create awsdev -d "AWS Developer Associate Certification" \
  --enable-issues=false --enable-wiki=false --public
```

```text
✓ Created repository br3ndonland/awsdev on GitHub
? Create a local project directory for br3ndonland/awsdev? Yes
✓ Initialized repository in './awsdev/'
```

## Resources

### Certifications

- [AWS certifications](https://aws.amazon.com/certification/)
- [freeCodeCamp: Pass the AWS Developer Associate exam with this free 16-hour course](https://www.freecodecamp.org/news/pass-the-aws-developer-associate-exam-with-this-free-16-hour-course/)
  - [Video 1](https://youtu.be/RrKRN9zRBWs) on YouTube
  - [Video 2](https://youtu.be/eCopK1RoyFM) on YouTube
  - If you would like to watch the videos offline, see [youtube-dl](https://github.com/ytdl-org/youtube-dl).
  - [Code](https://github.com/examproco/thefreeawsdeveloperassociate)

### General

- [AWS docs home](https://docs.aws.amazon.com/index.html)
- AWS What the Cloud _(recommended in the freeCodeCamp article)_
  - [YouTube](https://www.youtube.com/whatthecloud)
- Bart Castle _(recommended in the freeCodeCamp article)_
  - [YouTube](https://www.youtube.com/bartcastle)
  - [CBT Nuggets courses](https://www.cbtnuggets.com/trainers/bart-castle)

### DynamoDB

- [AWS DynamoDB docs](https://docs.aws.amazon.com/dynamodb/)
- [AWS CLI v2 docs: DynamoDB](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/dynamodb/index.html#cli-aws-dynamodb)
- [AWS Boto3 v1 docs: DynamoDB](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/dynamodb.html) - Boto3 is the Python SDK (Software Development Kit)
- Alex DeBrie
  - [Full Stack Radio podcast episode 2020 139](https://www.fullstackradio.com/episodes/139) 20200508
  - [DynamoDB Guide from Alex DeBrie](https://www.dynamodbguide.com)
  - AWS reinvent 2019: [Data modeling with Amazon DynamoDB](https://youtu.be/DIQVJqiSUkE), Alex DeBrie

### CloudFormation and infrastructure as code

- [Wikipedia: Infrastructure as code](https://en.wikipedia.org/wiki/Infrastructure_as_code)
- [AWS CloudFormation docs](https://docs.aws.amazon.com/cloudformation/index.html)
- [AWS CloudFormation docs: How does AWS CloudFormation work?](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-howdoesitwork.html)
- [AWS CloudFormation docs: CloudFormation template anatomy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html)
- AWS Quick Start ([AWS](https://aws.amazon.com/quickstart/), [GitHub](https://github.com/aws-quickstart)): CloudFormation templates for common AWS use cases
- [GitHub: awesome-cloudformation](https://github.com/aws-cloudformation/awesome-cloudformation)
- [AWS Toolkit VSCode extension](https://github.com/aws/aws-toolkit-vscode)
- [CloudFormation VSCode extension](https://github.com/aws-cloudformation/aws-cfn-lint-visual-studio-code)
- [AWS Boto3 v1 docs: CloudFormation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudformation.html)
- [Terraform docs: Terraform vs. CloudFormation](https://www.terraform.io/intro/vs/cloudformation.html)
- [Ansible docs: AWS](https://docs.ansible.com/ansible/latest/scenario_guides/guide_aws.html)

### AWS in biotech

- AWS reinvent 2019: [Creating life at scale with AWS](https://youtu.be/arDI64ja6KA), Dave Treff, Ginkgo Bioworks
- AWS reinvent 2019: [High-throughput production of mRNA](https://youtu.be/cxu2cD5FBcg), Dave Johnson, Moderna Therapeutics
