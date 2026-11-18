---
title: "AWS WAF (Frontend & Backend)"
weight: 4
chapter: false
pre: "<b> 5.7.4. </b> "
---

# 5.7.4. AWS WAF (Frontend & Backend)

> **Source status, as reported by the BTB team (18 November 2026):** WAF in use; backend limiting rules currently **Count**, not blocking.

## Objective and actual role

Web ACLs filter or count frontend CloudFront and backend ALB requests.

## Lab: inspect, document and verify the existing production setup

1. Open AWS WAF → Web ACLs; identify the CloudFront-scope (global) frontend ACL and the Regional ACL associated with ALB if present.
2. Inspect associations and verify each ACL protects the correct resource; a CloudFront ACL does not automatically cover API requests hitting ALB directly.
3. Record rules, priorities, conditions, managed rules and actions exactly as deployed.
4. For the **backend limiting rule**, explicitly record `Count` action, which records matches but does not itself terminate/block the request.
5. Open Traffic overview / sampled requests and collect benign evidence for CountedRequests; do not run abusive traffic to generate a screenshot.
6. Evaluate legitimate-traffic false positives before suggesting any future change to Block, and document the approval process.

## Expected outcome / result recording

**Expected:** Frontend and backend Web ACL associations match design and backend count-only rule records matches without claiming to block them.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Individual rule actions vary. A Count-only backend rule is not production blocking protection. WAF billing depends on ACL, rules and requests.

## Screenshot evidence to capture

CloudFront/ALB associations, rule action Count and sampled match counts.

**Suggested path:** `static/images/5-workshop/5.7.4-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/waf/latest/developerguide/web-acl-rule-actions.html>
