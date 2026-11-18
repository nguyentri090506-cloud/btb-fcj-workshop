---
title: "Amazon CloudWatch Logs"
weight: 1
chapter: false
pre: "<b> 5.8.1. </b> "
---

# 5.8.1. Amazon CloudWatch Logs

> **Source status, as reported by the BTB team (18 November 2026):** Backend logging configured.

## Objective and actual role

Centralized Spring Boot stdout/stderr logs for task startup, API issues and integrations.

## Lab: inspect, document and verify the existing production setup

1. Open CloudWatch → Logs → Log groups; locate the group named by the ECS task definition's awslogs configuration.
2. Inspect log streams for currently running ECS task(s) and verify timestamps match the latest production release.
3. Perform a non-destructive GET request on the real API; observe a corresponding operational trace/log event if application logging is designed for it.
4. Search for WARN/ERROR and identify common failures: DB connection, Bedrock permission, SePay webhook handler or SMTP delivery; redact any personal data.
5. Check log retention and expected ingestion cost; set retention with team approval rather than leaving lab logs indefinitely.
6. Capture a sanitized screenshot of log group, streams and one relevant event; never publish JWTs, emails, passwords or connection strings.

## Expected outcome / result recording

**Expected:** Logs are linked to the running task and support troubleshooting without leaking secrets.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

CloudWatch Logs are not a substitute for application-level business audit records.

## Screenshot evidence to capture

Task awslogs setup, log streams, sanitized error or health log.

**Suggested path:** `static/images/5-workshop/5.8.1-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html>
