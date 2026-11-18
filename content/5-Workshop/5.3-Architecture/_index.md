---
title: "Architecture & Data Flow"
weight: 3
chapter: false
pre: "<b> 5.3. </b> "
---

# 5.3. Production Architecture & Data Flow

Use an **AWS Architecture Diagram drawn and reviewed by the team in diagrams.net/draw.io with AWS 2026 Icons**. The screenshot below must be replaced by the final exported diagram **only after checking the actual production topology**. Do not use sample CIDRs, Region, two-AZ claims or NAT as verified facts unless the console confirms them.

**Expected file:** `static/images/5-workshop/architecture/btb-production-reviewed.png`.

## Logical architecture (not a verified subnet map)

```text
Users (Guest / Customer / Staff / Admin)
  |-- frontend hostname (Route 53) --> CloudFront + attached frontend WAF --> S3 React build
  |       |-- HTTPS cert: ACM (CloudFront certificate in us-east-1)
  |       `-- RUM browser client -> Cognito Identity Pool credentials -> CloudWatch RUM
  `-- API hostname (Route 53) --> ALB + attached Regional backend WAF [limiting rules: COUNT]
                                      --> ECS Fargate (Spring Boot, in VPC)
                                              |-- ECR image, Secrets Manager, IAM roles
                                              |-- Supabase PostgreSQL / reported Auth
                                              |-- Bedrock inference [production call pending test]
                                              |-- Cloudinary images
                                              |-- Vietmap maps and address/location
                                              |-- SePay QR and authenticated webhook callback
                                              `-- Gmail SMTP (application OTP)

CloudWatch Logs + Metrics/Alarms -> SNS -> operator email
AWS Budgets -> cost alert recipients
GitHub `feat/prod` -> Actions -> ECR/ECS (backend); S3/CloudFront (frontend)
```

## Separate flow types

1. **Frontend viewer:** Browser resolves DNS, establishes TLS to CloudFront and requests the SPA. S3 is an *origin*, not the browser's normal public HTTPS endpoint.
2. **API viewer:** Browser resolves API DNS and connects over HTTPS to ALB; Regional WAF is **associated** with ALB, not a separate proxy hop. ALB forwards to ECS task targets.
3. **Payment callback:** SePay calls the backend's configured webhook route. Backend validates authenticity, event identity and payment state before updating Order.
4. **Application email:** Spring Boot uses Gmail SMTP to send OTP; Amazon SNS is for alarm notifications, not OTP.
5. **Monitoring:** ECS logs flow to CloudWatch Logs; AWS metrics feed alarms/SNS. Browser RUM events use Cognito Identity Pool limited credentials.
6. **CI/CD:** GitHub Actions from `feat/prod` builds and deploys FE to S3/CloudFront and BE to ECR/ECS.

## Architecture validation checklist

- [ ] CloudFront, Route 53 and SNS are shown as AWS services *not contained within an individual VPC subnet*.
- [ ] The diagram distinguishes AWS Region-dependent resources from CloudFront global resources; ACM CloudFront cert uses us-east-1.
- [ ] Public/private subnet placement, AZs, NAT/egress and IAM boundaries exactly match AWS Console.
- [ ] Both WAF associations are represented, including backend **Count-only** rule action.
- [ ] External providers (Supabase, Cloudinary, Vietmap, SePay, Gmail SMTP) appear outside AWS Cloud boundary.
- [ ] Bedrock and RUM are labeled **pending validation** for production behavior.

See service details in 5.4–5.10. Do not publish a diagram containing unverified fake IP blocks or invented resources.
