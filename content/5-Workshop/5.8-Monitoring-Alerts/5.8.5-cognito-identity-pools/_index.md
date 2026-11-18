---
title: "Amazon Cognito Identity Pools"
weight: 5
chapter: false
pre: "<b> 5.8.5. </b> "
---

# 5.8.5. Amazon Cognito Identity Pools

> **Source status, as reported by the BTB team (18 November 2026):** Identity Pool created with RUM monitor.

## Objective and actual role

Issues AWS credentials for the browser RUM client as configured.

## Lab: inspect, document and verify the existing production setup

1. Open Amazon Cognito → Identity pools and locate the pool referenced by the RUM app monitor (not a User Pool used for BTB logins).
2. Inspect authentication/unauthenticated identities configuration as actually deployed and identify its IAM role.
3. Check the unauthenticated role policy grants only permissions needed for RUM ingestion (for example `rum:PutRumEvents` on the intended monitor), not generic AWS administrator access.
4. Confirm the deployed frontend uses the correct identity pool ID and Region without embedding AWS long-lived access keys.
5. Check browser telemetry requests and IAM access-denied messages; correlate with RUM ingestion status in the previous lab.
6. Document Cognito identity pools as **RUM-only**; do not equate them with Supabase/BTB Customer login or OTP activation.

## Expected outcome / result recording

**Expected:** Browser obtains permitted temporary credentials and RUM events reach intended app monitor (pending until verified).

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Cognito Identity Pools do not imply Cognito User Pools or customer auth is in use.

## Screenshot evidence to capture

Identity pool ID/Region, limited IAM role policy and RUM integration.

**Suggested path:** `static/images/5-workshop/5.8.5-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-RUM-get-started-authorization.html>
