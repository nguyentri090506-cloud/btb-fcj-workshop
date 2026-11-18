---
title: "Workshop"
weight: 5
chapter: false
pre: "<b> 5. </b> "
---

# Deploying Bite to Business on AWS — End-to-End Workshop

This workshop explains the **reported production architecture** and how to inspect, verify, troubleshoot and document it. It covers the whole team's AWS and non-AWS components rather than only one member's services. It follows the **Bite to Business (BTB)** application, a direct-sale food-commerce website serving both business customers and individuals/households. BTB is **not** a multi-vendor marketplace.

The frontend is React/TypeScript, delivered through **S3 → CloudFront**, with **Route 53, ACM and WAF**. The Java Spring Boot modular-monolith backend runs on **ECS with Fargate** behind an **Application Load Balancer**. Backend Docker images are stored in **ECR**. Operations use **IAM, Secrets Manager, CloudWatch Logs/Metrics/Alarms, SNS, Budgets, CloudWatch RUM and Cognito Identity Pools**. The team reports **Bedrock** model configuration. **Supabase, Cloudinary, Vietmap, SePay and Gmail SMTP** are external providers. **GitHub Actions** deploys frontend and backend from `feat/prod`.

**Evidence boundary:** production status is based on the team's inventory dated **18 November 2026**, not on direct read access to AWS. Bedrock production API invocation and RUM telemetry are explicitly **pending verification**; backend WAF limiting rules are set to **Count**, not Block. Historical project documents mention Gemini and disagree about Supabase Auth/JWT; inspect the active backend before claiming a definitive implementation.

**Scope exclusions:** SQS, SES, CodePipeline/CodeBuild, CloudTrail, NAT Gateway and VPC endpoints were mentioned in earlier plans, but were **not confirmed in the team's latest production inventory**. This workshop does not invent them as deployed resources.

## Navigation

- [5.1. Overview](5.1-overview/)
- [5.2. Prerequisites](5.2-prerequisites/)
- [5.3. Architecture & Data Flow](5.3-architecture/)
- [5.4. Network & Foundation](5.4-foundation/)
- [5.5. Container & Storage](5.5-containers-storage/)
- [5.6. Backend & AI Deployment](5.6-backend-ai/)
- [5.7. Web Delivery & Security](5.7-web-security/)
- [5.8. Monitoring & Alerts](5.8-monitoring-alerts/)
- [5.9. External Integrations](5.9-external-integrations/)
- [5.10. CI/CD Deployment](5.10-ci-cd/)
- [5.11. Testing & Live Demo](5.11-testing/)
- [5.12. Cost Estimation](5.12-cost/)
- [5.13. Cleanup & Troubleshooting](5.13-cleanup/)

## Evidence instructions

Each service page provides actual reported status, hands-on inspection steps, expected results, an empty actual-result field and screenshot suggestions. **Replace placeholders with your own dated AWS Console screenshots**, CI/CD run logs, redacted tests and domain details. Do not present an example as a test that already passed. Keep secrets and Customer records private.
