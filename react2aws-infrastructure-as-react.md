---
title: React2AWS - Infrastructure as React Components
anchor: Write AWS infrastructure using React/JSX with Tailwind className syntax, output Terraform
tags: [aws, infrastructure, react, terraform, iac, web]
description: Platform to write AWS infrastructure as React components with Tailwind-inspired syntax, generating production-ready Terraform
source_url: https://www.react2aws.xyz/
---

## My Reference

### Overview
**React2AWS** is a platform that reimagines Infrastructure as Code by letting you define AWS resources using React/JSX components with Tailwind-inspired `className` syntax. It outputs production-ready Terraform files.

### How It Works
1. Write JSX with Tailwind-style className for AWS resources
2. Generate Terraform (main.tf, variables.tf, outputs.tf, backend.tf)
3. Deploy infrastructure

### Supported Resources
Core AWS building blocks — with more coming (EKS, ElastiCache, SQS, SNS)

### Syntax Example
| Component | Attribute | Value |
|-----------|-----------|-------|
| Uses React component pattern | `className` for config | Tailwind-inspired syntax |

### Benefits
- **Familiar DX** — React developers feel at home
- **Clean syntax** — No verbose HCL/Terraform
- **Type safety** — React prop validation
- **Component reuse** — Build reusable infrastructure components
- **Studio available** — Interactive playground at /studio

### Resources
- **Site:** https://www.react2aws.xyz/
- **GitHub:** https://github.com/mmarinovic/React2AWS

### Similar Approaches
- **Pulumi** — TypeScript/YAML for infrastructure
- **AWS CDK** — TypeScript/Python for Terraform/CloudFormation
- **Terragrunt** — Terraform wrapper for composition
