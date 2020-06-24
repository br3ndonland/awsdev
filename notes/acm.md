# AWS Developer Associate: ACM

## freeCodeCamp ExamPro walkthrough

- [Video 1](https://youtu.be/RrKRN9zRBWs) 3.25.15
- SSL/TLS certificates
- Public certs are free
- **Private certs (certs you import) cost \$400/month**
- Encryption termination options:
  - At load balancer: can be attached to ELB, CloudFront, or API Gateway. Traffic between ELB/ALB and EC2 instances downstream is unencrypted.
  - Can also terminate SSL end-to-end. Traffic is encrypted all the way to the application. Can't do directly with ACM, has to be done with Letsencrypt directly on each EC2 instance.
