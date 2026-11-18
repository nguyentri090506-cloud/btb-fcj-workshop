---
title: "Gmail SMTP for System OTP"
weight: 5
chapter: false
pre: "<b> 5.9.5. </b> "
---

# 5.9.5. Gmail SMTP for System OTP

> **Source status, as reported by the BTB team (18 November 2026):** External mail service reported; actual delivered OTP must be tested separately from SNS alert email.

## Objective and actual role

Sends selected BTB system emails, particularly onboarding or password-reset OTPs.

## Lab: inspect, document and verify the existing production setup

1. Inspect backend mail settings (SMTP host, port, STARTTLS, sender address and credential sourcing) without printing the SMTP password or app password.
2. Verify the required secret is stored in Secrets Manager or another approved secret store and injected into the ECS task securely.
3. Using a test-only Gmail recipient, trigger the real BTB onboarding/reset flow: Admin approval → OTP sent → customer enters valid OTP → password activation/reset, as implemented.
4. Verify delivered message metadata, expiration/one-time behavior, rate limiting and non-disclosure of OTP in backend logs.
5. Test an invalid/expired OTP to confirm backend rejection and safe error responses; do not use production Customer records.
6. Document Gmail SMTP separately from AWS SNS: SNS sends CloudWatch alarms, SMTP sends application OTP.

## Expected outcome / result recording

**Expected:** Test inbox receives the authorized OTP and invalid/expired OTP fails as designed; secrets remain hidden.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

No real OTP, Gmail password or SMTP access credential belongs in a public workshop repository.

## Screenshot evidence to capture

Redacted successful test email, OTP test outcome, no credential exposure.

**Suggested path:** `static/images/5-workshop/5.9.5-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://support.google.com/accounts/answer/185833>
