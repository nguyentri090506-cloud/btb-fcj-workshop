---
title: "Cost Estimation"
weight: 12
chapter: false
pre: "<b> 5.12. </b> "
---

# 5.12. Cost Estimation & Optimization

Use the **[AWS Pricing Calculator](https://calculator.aws/)** and record the deployed Region, workload assumptions, monthly hours and usage. Do **not** invent a monthly bill. AWS Budgets threshold and AWS actual billing data are separate from a Calculator estimate.

## Cost input checklist

| Service | Usage/cost driver to measure | Actual |
|---|---|---|
| ECS Fargate | task count, vCPU, RAM GiB, run hours | TODO |
| ALB | active hours, LCU and processed traffic | TODO |
| ECR | image GB stored, scanning type, lifecycle | TODO |
| S3 | GB/month, request count, versioning | TODO |
| CloudFront | outbound GB by geography, requests, invalidations | TODO |
| Route 53 + ACM | hosted zone/queries, certificate type | TODO |
| Secrets Manager | secrets/month and API calls | TODO |
| CloudWatch Logs/Metrics/Alarms | log ingest/retention, custom metrics, alarms | TODO |
| SNS | notification message count | TODO |
| CloudWatch RUM | browser event ingestion/retention | TODO |
| Cognito Identity Pools | supported credential usage pattern; validate applicable charges | TODO |
| AWS WAF | web ACLs, rules, managed groups and requests | TODO |
| Amazon Bedrock | tokens/model pricing, inference method, Region | TODO |
| VPC networking | public IPv4, outbound data, optional NAT/endpoint only if deployed | TODO |
| AWS Budgets | applicable budget pricing/notifications | TODO |
| External providers | Supabase, Cloudinary, Vietmap, SePay, Gmail SMTP plans/usage | TODO (separate estimate) |

## Optimization decisions

1. Check real ECS CPU/memory and ALB metrics before right-sizing; keep availability limitations explicit if running one task/AZ.
2. Cache immutable frontend assets appropriately, and audit CloudFront data transfer.
3. Retain CloudWatch logs for a stated period; set ECR image lifecycle and S3 version retention as approved.
4. Review WAF sampled requests before changing backend rule from Count to Block.
5. Monitor Bedrock token consumption and RUM sampling/ingestion; neither is guaranteed free.
6. Attach a dated Calculator screenshot/export with assumptions and use Budgets to monitor actual spend.

**Deliverables:** Calculator URL/export, assumptions, service breakdown and optimization explanation. No numeric total is claimed until inputs are known.
