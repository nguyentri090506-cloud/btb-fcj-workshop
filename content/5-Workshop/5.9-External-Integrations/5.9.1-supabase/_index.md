---
title: "Supabase PostgreSQL & Authentication"
weight: 1
chapter: false
pre: "<b> 5.9.1. </b> "
---

# 5.9.1. Supabase PostgreSQL & Authentication

> **Source status, as reported by the BTB team (18 November 2026):** In production service inventory; exact Supabase Auth vs Spring Boot JWT ownership must be confirmed against running code.

## Objective and actual role

External PostgreSQL database and reported authentication component for BTB.

## Lab: inspect, document and verify the existing production setup

1. Open the Supabase project dashboard and record project Region and network policy without copying connection passwords or project service-role keys.
2. Confirm which backend connections use PostgreSQL directly and which use Supabase Auth; inspect current production Spring Security/JWT integration to resolve the historical document conflict.
3. Verify private ECS tasks can connect to Supabase over TLS using the approved outbound route and correct DNS/port.
4. Use a read-only, test-data query through the real Spring Boot API; inspect error logs if DNS, TLS, pool or timeout fails.
5. Test a non-sensitive login/onboarding scenario against the actual current auth owner, distinguishing OTP activation from JWT authorization.
6. Ensure browser-side public keys are not confused with service-role keys, and restrict access to Customer/Staff data on the backend.

## Expected outcome / result recording

**Expected:** Database connectivity and auth behavior have real evidence; architecture records who actually issues/verifies tokens.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Master context has contradictory Supabase Auth descriptions. The user-provided production list is newer, but code/config must resolve the exact implementation.

## Screenshot evidence to capture

Project settings (redacted), backend connection success and test auth response.

**Suggested path:** `static/images/5-workshop/5.9.1-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://supabase.com/docs/guides/database/overview>
