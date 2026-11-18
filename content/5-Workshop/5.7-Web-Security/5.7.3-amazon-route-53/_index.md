---
title: "Amazon Route 53"
weight: 3
chapter: false
pre: "<b> 5.7.3. </b> "
---

# 5.7.3. Amazon Route 53

> **Source status, as reported by the BTB team (18 November 2026):** DNS configured.

## Objective and actual role

DNS records direct frontend and API hostnames to CloudFront and ALB.

## Lab: inspect, document and verify the existing production setup

1. Open Route 53 → Hosted zones; identify the actual public zone for the BTB domain.
2. Record the frontend hostname's alias/CNAME target and ensure it points to CloudFront distribution domain as configured.
3. Record the API hostname's alias target and ensure it points to the Application Load Balancer DNS name.
4. Check TTL values if used and verify DNS validation records required by ACM are present and maintained.
5. Use `Resolve-DnsName` or `nslookup` on both live names; compare actual answers to intended service targets.
6. Test HTTPS responses to both hostnames and document the resulting frontend/API behavior.

## Expected outcome / result recording

**Expected:** DNS for FE and API resolves correctly and HTTPS serves the intended service.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

DNS names, hosted zones and domains are placeholders until the team supplies real verified values.

## Screenshot evidence to capture

Hosted zone records, resolved targets and browser HTTPS checks.

**Suggested path:** `static/images/5-workshop/5.7.3-01.png` (capture from real Console; do not create a fake screenshot).

## Optional read-only command

```powershell
# Windows PowerShell — replace with actual public names
Resolve-DnsName <FRONTEND_DOMAIN>
Resolve-DnsName <API_DOMAIN>
```

## Official reference

<https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html>
