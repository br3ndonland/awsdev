# API Gateway

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)

## freeCodeCamp ExamPro walkthrough

[Video 2](https://youtu.be/eCopK1RoyFM) 2.18.30

- **API Gateway**:
  - Solution for scaling cloud APIs
  - Provides a base URL, and can route endpoints to various other services
  - Throttles API endpoints at 10,000 requests per second _(potential exam question)_
  - Authorization can be implemented with AWS Cognito or a custom Lambda.
- **Stages** are published versions of your API.
- **CORS** is enforced by the client (browser) and can be enabled on all endpoints or individual ones
- **Same-origin policies** prevent cross-site scripting (XSS).
