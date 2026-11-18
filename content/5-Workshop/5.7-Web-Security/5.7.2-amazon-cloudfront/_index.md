---
title: "Amazon CloudFront"
weight: 2
chapter: false
pre: "<b> 5.7.2. </b> "
---

# 5.7.2. Amazon CloudFront

> **Source status, as reported by the BTB team (18 November 2026):** Frontend distribution active.

## Objective and actual role

Delivers the React SPA from S3 with HTTPS, caching and WAF integration.

## Lab: inspect, document and verify the existing production setup

1. Open CloudFront → Distributions; select the frontend production distribution and record its ID, alternate domain, status and default behavior.
2. Verify origin points to the intended S3 bucket and inspect Origin Access Control/bucket access if used.
3. Check viewer certificate, HTTPS redirect, cache policy and response behavior for static assets.
4. Review SPA routing fallback: confirm React deep links work, using app-compatible CloudFront custom errors/functions/rewrite (do not blindly turn all 403s into index.html if it hides real failures).
5. Check the attached frontend AWS WAF web ACL separately from the backend ALB WAF.
6. Verify content through the real domain, then inspect cache invalidation from GitHub Actions after deployment.

## Expected outcome / result recording

**Expected:** Frontend domain returns page/assets over HTTPS and nested routes work on refresh.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

CloudFront is global; do not place it as a resource *inside* a single VPC subnet in the final diagram.

## Screenshot evidence to capture

Distribution status, origin, TLS and browser network requests.

**Suggested path:** `static/images/5-workshop/5.7.2-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html>
