---
title: "Amazon Bedrock"
weight: 4
chapter: false
pre: "<b> 5.6.4. </b> "
---

# 5.6.4. Amazon Bedrock

> **Source status, as reported by the BTB team (18 November 2026):** Model access and IAM role configured; production backend AI endpoint still needs an end-to-end check.

## Objective and actual role

AI model inference for BTB backend actions/Generate UI where connected; business authorization stays in Spring Boot.

## Lab: inspect, document and verify the existing production setup

1. Open Amazon Bedrock in the actual Region and record the enabled/available model ID or inference profile used by the application (subject to regional access).
2. Inspect the ECS task role IAM policy for the model invocation operations and resource restrictions needed by this model/profile.
3. Check the backend model-provider configuration in Secrets Manager/ECS runtime without printing API keys, prompts containing personal data or credentials.
4. Use a non-sensitive, test-only request against the **real** backend AI endpoint; if the endpoint path is unknown, first locate it in Swagger/OpenAPI rather than inventing one.
5. Check backend/Bedrock invocation logs and latency; separate model permission errors, timeout, throttling and application validation failures.
6. Record status honestly: configured versus verified on production; explain that AI cannot directly approve Quotes, change price, reserve stock or authorize orders.

## Expected outcome / result recording

**Expected:** A safe test request reaches the backend AI endpoint and returns an authorized, schema-valid result; otherwise report it as pending.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Historical planning documents mentioned Gemini; the latest team status says Bedrock is configured. Confirm the actual backend provider before removing historical mentions.

## Screenshot evidence to capture

Model/profile config, IAM policy scope, sanitized test response and logs.

**Suggested path:** `static/images/5-workshop/5.6.4-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html>
