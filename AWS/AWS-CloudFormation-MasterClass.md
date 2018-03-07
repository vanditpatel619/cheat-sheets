# CloudFormation Master Class

## What is CloudFormation

Having >50 services, CloudFormation was brought in to help develops scaffold out the requires AWS stack.

Eg. I want a security group, two EC2 machines with it, two elastic IPs, an S3 bucket + a load balancer in front.

CloudFormation will create all of this in the right order with the exact config.

## Benefits 

1. Infrastructure as code  
    - No manual creation
    - Can be version controlled 
    - Changes to infrastructure are reviewed through code
2. Cost 
    - Each resource will be tagged so you can estimate the costs and figure out which costs what
    - Great savings strategy 
3. Productivity
    - Ability to destroy and re-create an infrastructure
    - Automated generation of Diagram for templates 
    - All declarative 
4. Separation of concern
    - Many different stacks for many different layers 
5. Don't re-invent the wheel
    - Already so many templates
    - Leverage the docs

## CloudFormation vs Ansible / Terraform

- CF is native, and also contain the latest 
- CF is state based
- The others are instruction based - difficult to orchestrate 
- For new services, Ansible / Terraform can take a long time

## First template

```yaml
---
Resources:
  MyInstance:
    Type: AWS::EC2::Instance
    Properties:
      AvailabilityZone: us-east-1a
      ImageId: ami-a4c7edb2
      InstanceType: t2.micro
```

The stack instance can be created, updated or destroyed.

You cannot edit the stack itself later, you need to just re-update the stack by uploading a new file.

The stack itself can clean up instances after itself too.