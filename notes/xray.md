# AWS Developer Associate: X-Ray

## freeCodeCamp ExamPro walkthrough

[Video 1](https://youtu.be/RrKRN9zRBWs) 2.55.20

- [AWS X-Ray](https://aws.amazon.com/xray/) is a performance monitoring system, basically monitoring **microservices** like DataDog does.
- For Node.js, .NET, Java, Go, Python, Ruby, and PHP
  - 3.24.45: "As long as they're not getting Perl on the list, it should be pretty easy to figure that out."
- Works with EC2, ECS, Fargate, Elastic Beanstalk, and Lambda. Can also integrate SNS (simple notification service) and SQS (simple queue service)
- X-Ray SDK for Node, Python, Ruby
- Use the SDK to capture **segments**. Segments are basically API calls you enclose within a segment to tell X-Ray when to start and stop monitoring.
- X-Ray daemon gathers data from UDP port 2000
- X-Ray doesn’t record every request. It does **sampling** of the first request each second, then 5% of additional requests. This reduces service costs.
- X-Ray groups segments with a request in common into **traces**. Each trace gets a trace ID. An HTTP header `X-Amzn-Trace-Id` is added.
- The traces are processed into a **service graph** showing relationships among the microservices. The service graph helps identify bottlenecks.
  - **Filter expressions** help narrow down the graph.
  - **Annotations** are key:value pairs that are indexed for use with filter expressions. There is a limit of 50 annotations per trace.
  - **Metadata** can store non-indexed key:value pairs. Values can be of any type, including objects and lists.
- **Errors are 400**
- **Faults are 500**
- **Throttle is 429 Too Many Requests**
- 3.03.45 Typo: “Deamon”
