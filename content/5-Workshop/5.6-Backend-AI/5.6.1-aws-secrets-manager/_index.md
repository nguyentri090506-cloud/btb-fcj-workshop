---
title: "AWS Secrets Manager"
weight: 1
chapter: false
pre: "<b> 5.6.1. </b> "
---

# 5.6.1. AWS Secrets Manager

> **Source status, as reported by the BTB team (18 November 2026):** Backend secret has been created; field schema/access mapping requires verification.

## Objective and actual role

Protects backend connection parameters, AI configuration, webhook credentials and mail secrets.

## Lab: inspect, document and verify the existing production setup

1. Open Secrets Manager → Secrets and locate the existing backend secret by name, not by its secret value.
2. Verify Region, secret name/ARN, rotation configuration (if any), last modified date and KMS settings where applicable.
3. Open ECS task definition → Container → Secrets; verify the reference to each required secret key/environment name, or document app-side retrieval if that design is used.
4. Confirm ECS task execution role can fetch task-definition secrets; if the app fetches them at runtime, verify task-role access separately.
5. Check backend logs contain no secret values or raw connection strings, and document secure redeploy after a credential change.
6. Record only secret names and configuration shape; never capture or publish the `Retrieve secret value` screen.

## Expected outcome / result recording

**Expected:** Secret references are resolved by the correct role, and a newly started backend task can initialize without exposed credentials.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Restarting a task may be needed to pick up changed injected environment secrets; do not assume live rotation.

## Screenshot evidence to capture

Secret metadata and ECS secret references with values hidden.

**Suggested path:** `static/images/5-workshop/5.6.1-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/AmazonECS/latest/developerguide/specifying-sensitive-data-secrets.html>
