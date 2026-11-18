---
title: "Prerequisites"
weight: 2
chapter: false
pre: "<b> 5.2. </b> "
---

# 5.2. Prerequisites

**This workshop targets inspection and verification of an existing production deployment.** Do not recreate running resources with the same name. Work in a dedicated lab account where experimentation could change or delete resources.

## Access and tooling

1. AWS account with read access to VPC, ECS, ECR, S3, ALB, ACM, Route 53, WAF, CloudWatch, SNS, RUM, Cognito, IAM, Secrets Manager and Bedrock. Ask the owner for a role with least privilege; mutation requires approval.
2. GitHub access to the FE/BE repositories and the existing `feat/prod` Actions workflow; Docker for local container verification; Java/Spring Boot + Node/npm for builds; PowerShell, `git`, optional AWS CLI and `curl`.
3. Real (redacted) FE/API domain names, AWS Regions, ECS cluster/service, ECR repository, S3 bucket, CloudFront distribution, ALB target group, SNS topic and RUM monitor names.
4. Test-only Customer/Staff/Admin accounts or a safe demo dataset; never publish true customer records or use real transactions for destructive tests.
5. Screenshots should show relevant resource configuration, current date where possible, expected and observed outcomes; mask ARNs/account identifiers if policy requires and **always redact secret values**.

## Environment facts to fill before proceeding

| Variable | Example / requirement | Actual |
|---|---|---|
| `AWS_REGION` | e.g. choose the actual backend Region | TODO |
| `FRONTEND_DOMAIN` | Actual HTTPS frontend | TODO |
| `API_DOMAIN` | Actual HTTPS API hostname | TODO |
| `ECS_CLUSTER`, `ECS_SERVICE` | Existing production names | TODO |
| `ECR_REPOSITORY`, `S3_BUCKET` | Existing image/static site stores | TODO |
| `BEDROCK_MODEL_ID` | Actual model or inference profile | TODO |
| `RUM_MONITOR`, `SNS_TOPIC` | Existing monitoring resources | TODO |

## Safety preparation

Request approval before changing WAF mode, IAM grants, security groups, deployment tasks, database, payment callbacks or DNS records. Use read-only inspection first. Store evidence in `static/images/5-workshop/` with no credentials.
