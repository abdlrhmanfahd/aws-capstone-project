# aws-capstone-project
Production-ready AWS infrastructure for a highly available and scalable multi-tier web application, built using VPC, public/private subnets, NAT gateways, Internet Gateway, ALB, EC2, Auto Scaling Groups, and IAM roles. Designed following AWS best practices with clean architecture and security in mind.

# AWS Capstone Project - Multi-Tier Web App

This repository contains a complete infrastructure-as-a-service (IaaS) project on AWS for a highly available multi-tier web application. The project includes:

- Custom VPC with CIDR 10.0.0.0/16
- 2 Public and 2 Private Subnets across multiple AZs
- NAT Gateways, Internet Gateway, and Route Tables
- EC2 Web Servers with Apache installed via user-data
- Application Load Balancer with Target Group
- Auto Scaling Group with Launch Template
- IAM Role for EC2 to use SSM
- Security Groups with least privilege access
- Cleanup instructions to avoid charges

## Architecture Diagram

![architecture](architecture.png)


## Notes
- Region: US-EAST-1
- EC2 Type: t2.micro
- OS: Amazon Linux 2023

## Key Highlights

- Multi-AZ, multi-subnet VPC architecture
- Full isolation between tiers
- Highly available and scalable setup
- IAM roles and least privilege access
- Built 100% using AWS Console (manual)

## User Data Script

```bash
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "This is an app server in AWS Region US-EAST-1" > /var/www/html/index.html
