---
title: "Amazon ECS with AWS Fargate"
weight: 3
chapter: false
pre: "<b> 5.6.3. </b> "
---

# 5.6.3. Amazon ECS with AWS Fargate

> **Source status, as reported by the BTB team (18 November 2026):** Backend running in production.

## Objective and actual role

Runs the modular-monolith Spring Boot API as a managed container workload.

## Lab: inspect, document and verify the existing production setup

1. Open ECS → Clusters → select BTB cluster → Services; record actual desired/running/pending task counts and deployment state.
2. Open service task definition revision; document image URI, port mapping, CPU/memory, Fargate platform, task execution role, task role and logging configuration.
3. Verify network attachments (subnets/security groups/public-IP setting) and their relationship to ALB target group.
4. Check ECS deployment events and task health; compare running image digest with ECR and confirm log stream is present in CloudWatch Logs.
5. Use safe production API tests (read-only catalog or authentication request with test account), without submitting real orders or exposing user data.
6. Explain restart/rollback path: select a prior **verified** task revision or image digest, update service, monitor healthy targets; do not trigger rollback merely for a documentation test.

## Expected outcome / result recording

**Expected:** Running task count meets desired count, ALB sees healthy targets and corresponding container logs exist.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Running one task or one AZ may be valid for a low-cost demo but must not be described as highly available.

## Screenshot evidence to capture

ECS service, active tasks, task definition, service events.

**Suggested path:** `static/images/5-workshop/5.6.3-01.png` (capture from real Console; do not create a fake screenshot).

## Optional read-only command

```powershell
# CLI read-only example; replace placeholders
aws ecs describe-services --cluster <CLUSTER> --services <SERVICE> --region <AWS_REGION>
```

## Official reference

<https://docs.aws.amazon.com/AmazonECS/latest/developerguide/what-is-fargate.html>
