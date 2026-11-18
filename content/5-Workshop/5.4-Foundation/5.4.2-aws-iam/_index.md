---
title: "AWS IAM"
weight: 2
chapter: false
pre: "<b> 5.4.2. </b> "
---

# 5.4.2. AWS IAM

> **Source status, as reported by the BTB team (18 November 2026):** Roles exist; review actual trust policies and least-privilege grants.

## Objective and actual role

Permissions for ECS task execution, backend runtime Bedrock access and GitHub Actions deployment.

## Lab: inspect, document and verify the existing production setup

1. Open IAM → Roles and identify the ECS task execution role, ECS task role, and CI/CD deployment role by their actual names.
2. Inspect task execution role permissions needed to read ECR images, write CloudWatch logs and access referenced task-definition secrets.
3. Inspect application task role separately; verify permitted Bedrock actions/model resources only as required by the backend.
4. For GitHub Actions, inspect the OIDC provider and deployment-role trust policy; restrict `sub` to the intended repository and `feat/prod` branch if the workflow uses OIDC.
5. Review IAM policy JSON and CloudTrail/last-used information if available; remove overly broad policies only after teammate review.
6. Document what each role does and keep IAM distinct from BTB Guest/Customer/Staff application authorization.

## Expected outcome / result recording

**Expected:** Roles and trust relationships are separated; task role has only required Bedrock permissions; CI/CD is not using committed long-lived credentials.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Do not upload IAM credentials, private key material or unredacted role session tokens.

## Screenshot evidence to capture

Role names, trust-policy summary and policy attachments (redacted).

**Suggested path:** `static/images/5-workshop/5.4.2-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html>
