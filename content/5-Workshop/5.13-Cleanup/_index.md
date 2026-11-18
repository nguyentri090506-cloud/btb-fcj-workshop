---
title: "Cleanup & Troubleshooting"
weight: 13
chapter: false
pre: "<b> 5.13. </b> "
---

# 5.13. Cleanup & Troubleshooting

## Important: production safeguards

**Do not delete or disable running production resources to complete a workshop cleanup.** Cleanup applies only to **dedicated lab resources** with explicit permission. Keep the team-shared production VPC, ECS, ALB, Route 53, CloudFront, S3, ECR, WAF, Secrets Manager, IAM, Budgets, RUM, Cognito, Bedrock and monitoring resources intact.

## Dependency-aware lab cleanup (lab only)

1. Archive redacted test evidence and write down resource IDs/cost measurements.
2. Remove lab ECS services/tasks after approved stop; remove related ALB listener/target group and dedicated load balancer.
3. Remove lab CloudFront distribution associations, disable then delete when the distribution state allows it; detach lab WAF Web ACLs first.
4. Remove lab S3 bucket objects/versions, then its bucket **only if separate from production**.
5. Remove unused lab ECR images/repositories and lab secrets (respect scheduled deletion recovery window).
6. Clean only test-specific IAM roles, log groups, SNS topics, alarms, RUM app monitors/Cognito pools and Route 53 records after verifying no shared dependency.
7. Record residual recurring charges, domain registration and external-provider subscriptions; review Cost Explorer as billing updates asynchronously.

## Failure scenarios and quick diagnosis

| Symptom | Start checking |
|---|---|
| Website returns 403/404 on refresh | CloudFront origin/OAC and SPA routing |
| API 502/503 | ALB target health, ECS port/SG, task logs |
| ECS `CannotPullContainerError` | ECR image URI, execution role, outbound/ECR networking |
| Backend cannot connect Supabase | TLS/DNS, network egress, secret, connection pool |
| Bedrock AccessDenied | Region/model availability, task role IAM, model profile |
| WAF rule shows matches but request still passes | Action may be **Count**, not Block |
| CloudWatch Alarm has no email | alarm action → SNS topic, Confirmed subscription, mailbox |
| CloudWatch RUM no data | FE code deployed, domain allow-list, Cognito role, browser telemetry |
| SePay callback fails | HTTPS URL/routing, provider authentication, idempotency, app logs |
| Gmail OTP missing | SMTP/TLS/credentials, recipient, rate limit and safe logs |
| Hugo local build fails | Installed Hugo version vs theme, deprecated `getJSON` shortcode |

## Completion checklist

- [ ] Each service has actual screenshots and resource IDs.
- [ ] Real test outcomes are recorded, including unresolved failures.
- [ ] Final team-reviewed draw.io architecture is exported and dated.
- [ ] Pricing Calculator and live-demo evidence are attached.
- [ ] No secrets/Customer PII in GitHub.
