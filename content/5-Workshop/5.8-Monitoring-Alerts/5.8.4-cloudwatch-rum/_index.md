---
title: "CloudWatch RUM"
weight: 4
chapter: false
pre: "<b> 5.8.4. </b> "
---

# 5.8.4. CloudWatch RUM

> **Source status, as reported by the BTB team (18 November 2026):** App monitor created and FE code added; ingestion of actual browser data remains unverified.

## Objective and actual role

Browser-side monitoring for React performance and JavaScript errors.

## Lab: inspect, document and verify the existing production setup

1. Open CloudWatch → Application Signals / RUM (console label may vary) and identify the production app monitor, its Region and monitored domain.
2. Inspect the app monitor configuration: included origins/domains, collected telemetry types, sample rate and any allowed data storage settings.
3. Inspect React's deployed frontend build to confirm the RUM client snippet/SDK initializes in production, not just in a local branch.
4. Check Cognito Identity Pool credentials used by the RUM SDK and inspect browser DevTools Network/Console for blocked telemetry requests or CORS errors.
5. Visit the live frontend with consent/privacy settings respected, navigate a few non-sensitive pages, then inspect RUM app monitor for page views/performance/errors.
6. If no new data appears, record `Pending verification`, the investigated timestamp and potential causes; do not claim RUM success based only on creating a monitor.

## Expected outcome / result recording

**Expected:** RUM console shows recent page views/errors from the live domain, otherwise the check remains pending.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

RUM frontend SDK may capture URLs/metadata; avoid leaking personal information and review privacy/consent settings.

## Screenshot evidence to capture

App monitor settings, FE SDK code location, sanitized network requests, RUM dashboard.

**Suggested path:** `static/images/5-workshop/5.8.4-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-RUM-get-started.html>
