---
title: "CloudWatch Metrics & Alarms"
weight: 2
chapter: false
pre: "<b> 5.8.2. </b> "
---

# 5.8.2. CloudWatch Metrics & Alarms

> **Source status, as reported by the BTB team (18 November 2026):** Metrics and alarms configured.

## Objective and actual role

Track ECS CPU/memory, ALB errors/latency/healthy targets and trigger alert actions.

## Lab: inspect, document and verify the existing production setup

1. Open CloudWatch → Metrics; select the relevant ECS Cluster/Service metrics and ALB metrics for actual deployed resources.
2. Inspect current widgets for ECS CPUUtilization/MemoryUtilization, ALB HTTPCode_Target_5XX_Count, TargetResponseTime and HealthyHostCount as applicable.
3. Open Alarms → All alarms and record each production alarm's name, metric, period, statistic, evaluation periods and threshold.
4. Check `Actions` and confirm the alarm publishes to the intended SNS topic; verify `OK`, `ALARM`, or `INSUFFICIENT_DATA` state honestly.
5. If the team already conducted a safe alarm test, attach the real timestamped history and email; otherwise treat triggering as unverified and avoid modifying production thresholds solely for a demo.
6. Correlate alarm events with ECS events and CloudWatch Logs to explain root cause rather than only reporting graph changes.

## Expected outcome / result recording

**Expected:** Actual alarms and topics are documented and metric graphs align with running resource identifiers.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

No synthetic alarm success should be reported without an observed alarm transition and notification.

## Screenshot evidence to capture

Metric graph, alarm settings/state/history, linked SNS topic.

**Suggested path:** `static/images/5-workshop/5.8.2-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html>
