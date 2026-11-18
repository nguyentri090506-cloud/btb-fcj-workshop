---
title: "Application Load Balancer"
weight: 2
chapter: false
pre: "<b> 5.6.2. </b> "
---

# 5.6.2. Application Load Balancer

> **Source status, as reported by the BTB team (18 November 2026):** Operating in production.

## Objective and actual role

HTTPS API entry point forwarding requests to healthy ECS targets.

## Lab: inspect, document and verify the existing production setup

1. Open EC2 → Load Balancers and record the production Application Load Balancer's name, scheme and VPC.
2. Check listeners: which ports/protocols are enabled, whether HTTPS 443 is attached to a valid ACM certificate, and any HTTP→HTTPS redirect rule.
3. Open Target groups and verify protocol/port, **IP** target type for awsvpc Fargate tasks, configured health-check path and success codes.
4. Inspect registered targets; confirm desired ECS tasks are healthy and note any unhealthy reason rather than guessing.
5. Review ALB security group inbound rules and ECS task SG source restrictions; ensure direct access to backend task port is not public.
6. Use your actual API domain to test a safe read-only endpoint; capture status, TLS and routing evidence.

## Expected outcome / result recording

**Expected:** HTTPS listener is valid, healthy target registration matches ECS tasks, and API responds through ALB.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

For an ALB-direct API, a WAF on CloudFront does not protect this API; associate a separate Regional Web ACL.

## Screenshot evidence to capture

ALB listeners, target health, target type IP, and safe API response.

**Suggested path:** `static/images/5-workshop/5.6.2-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/AmazonECS/latest/developerguide/alb.html>
