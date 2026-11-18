---
title: "AWS Certificate Manager (ACM)"
weight: 1
chapter: false
pre: "<b> 5.7.1. </b> "
---

# 5.7.1. AWS Certificate Manager (ACM)

> **Source status, as reported by the BTB team (18 November 2026):** Certificates issued and used.

## Objective and actual role

TLS certificates for frontend CloudFront domain and backend ALB API domain.

## Lab: inspect, document and verify the existing production setup

1. Open ACM; inspect frontend certificate in **us-east-1** for CloudFront custom domain and note the exact domain coverage/validation status.
2. Switch to the ALB Region; inspect the API certificate issued for the backend hostname.
3. Verify both certificates are `Issued`, cover their live hostnames and have appropriate renewal/validation mechanism.
4. Inspect CloudFront Viewer certificate and ALB HTTPS listener to confirm the respective ACM certificate is actually attached.
5. Test frontend and API hostnames over HTTPS in a browser or `curl`; verify no hostname mismatch or certificate warning.
6. Record expiration/renewal status without exposing any private key material.

## Expected outcome / result recording

**Expected:** Two HTTPS paths use matching certificates and resolve without browser warnings.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

CloudFront custom certificate is in us-east-1; ALB uses a certificate from its own Region.

## Screenshot evidence to capture

Certificate metadata and CloudFront/ALB association; live HTTPS lock.

**Suggested path:** `static/images/5-workshop/5.7.1-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cnames-and-https-requirements.html>
