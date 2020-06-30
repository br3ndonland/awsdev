# AWS Developer Associate: VPC

## Table of Contents <!-- omit in toc -->

- [freeCodeCamp ExamPro walkthrough](#freecodecamp-exampro-walkthrough)
  - [Intro](#intro)
  - [Core components](#core-components)
  - [Key features](#key-features)
  - [Default VPC](#default-vpc)
  - [VPC peering](#vpc-peering)
  - [VPC endpoint](#vpc-endpoint)
  - [Route table](#route-table)
  - [Internet gateway](#internet-gateway)
  - [Bastion](#bastion)
  - [Autoscaling Group](#autoscaling-group)
  - [Direct Connect](#direct-connect)

## freeCodeCamp ExamPro walkthrough

### Intro

[Video 1](https://youtu.be/RrKRN9zRBWs) 7.10.15

- **VPC = Virtual Private Cloud**
- **VPC is important to know for all AWS certifications.**
- A VPC is a logically isolated portion of the AWS cloud, which contains resources in a virtual network you define.

### Core components

- Internet Gateway
- Virtual Private Gateway (VPN Gateway)
- Routing Table
- Network Access Control List (NACL)
- Security Group
- Public Subnet
- Private Subnet
- Nat Gateway
- Customer Gateway
- VPC Endpoint
- VPC Peering

### Key features

- VPCs are region-specific
- Max 5 VPCs per region (per account?)
- Max 200 subnets per VPC

### Default VPC

- AWS has a [default VPC](https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html) set up in every region, so you can immediately provision resources without setting up a VPC.
- AWS sets up the default VPC like this:
  - Create a VPC with a size `/16` IPv4 CIDR block (`172.31.0.0/16`). This provides up to 65,536 private IPv4 addresses.
  - Create a size `/20` default subnet in each Availability Zone. This provides up to 4,096 addresses per subnet, a few of which are reserved for our use.
  - Create an [internet gateway](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html) and connect it to your default VPC.
  - Create a default security group and associate it with your default VPC.
  - Create a default network access control list (ACL) and associate it with your default VPC.
  - Associate the default DHCP options set for your AWS account with your default VPC.
- The default IP is `0.0.0.0/0`. It represents all possible IP addresses. It is sometimes used to allow internet access by specifying in a route table or in the inbound rules of a security group.

### VPC peering

- Connect VPCs together directly using private IPs
- Can connect VPCs across accounts and regions, but can't have overlapping CIDR blocks.

### VPC endpoint

- A VPC endpoint connects a VPC to other AWS services.
- Interface endpoints provision an Elastic Network Interface (ENI) with a private IP address. They are powered by AWS PrivateLink. Interface endpoints cost extra.
- Gateway endpoints are used for S3 and DynamoDB. They specify targets for specific routes in your route tables. Gateway endpoints are free.

### Route table

- Route tables define how network traffic is directed
- Each VPC subnet must be associated with (only) one route table

### Internet gateway

- Controls access to the public internet
- Provides a target in VPC route tables for internet-routable traffic (`0.0.0.0/0`)
- Performs NAT (network access translation) for instances with public IPv4 addresses.

### Bastion

- Bastions or "jumpboxes" are hardened EC2 instances which are sometimes put in front of the other EC2 instances in a VPC. Users can SSH into a bastion instead of directly into the EC2 instances.

### Autoscaling Group

- An **Autoscaling Group (ASG)** is a collection of EC2 instances that can be automatically scaled in response to **triggers**:
  - Capacity settings: launching EC2 instances to meet a minimum value
  - Health checks:
    - If EC2 instances are unhealthy, EC2 can launch more.
    - The ELB can also hit endpoints to perform health checks.
  - Scaling policies:
    - Target scaling: maintaining target metrics, such as CPU usage, within target ranges
    - Simple scaling: legacy
    - Scaling with steps:
- A **Launch Configuration** is a template for EC2 instances that the ASG uses to launch. Can't be edited after creation (clone the config to create a new one).
- ELB integration
  - Classic Load Balancers (CLBs) associated with ASGs directly
  - ALBs and NLBs associate with ASGs indirectly, with a target group in between

### Direct Connect

- [Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html) provides dedicated fiber connections to AWS, bypassing ISPs.
- Very useful for enterprise
