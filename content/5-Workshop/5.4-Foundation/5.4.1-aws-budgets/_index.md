---
title: "AWS Budgets"
weight: 1
chapter: false
pre: "<b> 5.4.1. </b> "
---

# 5.4.1. AWS Budgets

> **Source status, as reported by the BTB team (18 November 2026):** Budget created; amount, threshold and destination must be verified.

## Objective and actual role

Cost visibility and alert thresholds for BTB production resources.

## Lab: inspect, document and verify the existing production setup

1. Open Billing and Cost Management → Budgets → inspect the existing BTB budget before editing it.
2. Record budget type (cost), period (monthly), currency, scope, and forecast or actual thresholds.
3. Check email subscribers and whether each notification is confirmed and reaches the intended team mailbox.
4. Inspect the latest actual/forecast spend and compare with ECS, ALB, CloudFront, WAF and logging usage.
5. If a dedicated lab budget is missing, create a cost budget with a clearly documented *example* threshold chosen by the team, not an invented production amount.
6. Capture screenshots with amounts obscured only if project policy requires; never claim an alert fired without an actual email.

## Expected outcome / result recording

**Expected:** Budget exists; thresholds and destinations match recorded values; notification is observable when actually triggered.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Budgets is not a hard spending cap; production resources keep incurring charges.

## Screenshot evidence to capture

Budget configuration, notification subscriptions, and cost trend.

**Suggested path:** `static/images/5-workshop/5.4.1-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html>
