---
title: "SePay QR & Payment Webhook"
weight: 4
chapter: false
pre: "<b> 5.9.4. </b> "
---

# 5.9.4. SePay QR & Payment Webhook

> **Source status, as reported by the BTB team (18 November 2026):** External payment integration listed; actual paid-order transition and callback validation require evidence.

## Objective and actual role

Provides bank transfer QR information and asynchronous payment-event callbacks.

## Lab: inspect, document and verify the existing production setup

1. Inspect the backend integration configuration for SePay endpoint, merchant/account mapping and webhook callback URL; redact all tokens and bank identifiers as required.
2. Trigger a **sandbox or team-authorized low-risk test** to obtain QR information; confirm amount/order reference uses backend-controlled values, not browser-provided payment confirmation.
3. Inspect the webhook route in the deployed backend and verify the provider's currently supported authentication/signature or shared-secret mechanism from its official integration specification.
4. Test a valid callback in the provider-supported test environment; check exact order reference matching, amount/currency validation, idempotency and replay protection.
5. Confirm malformed/duplicate callbacks do not mark an unpaid Order as paid or create duplicate inventory/shipping transitions.
6. Review sanitized webhook log entries in CloudWatch and record final payment state; never display customer bank data or treat a QR image as proof of payment.

## Expected outcome / result recording

**Expected:** Authorized payment event is matched and processed once; duplicate/invalid callback cannot forge paid state.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Provider webhook security must be verified against the current SePay integration contract; do not assume a particular signature header.

## Screenshot evidence to capture

QR test/reference (redacted), webhook config, valid/invalid callback logs.

**Suggested path:** `static/images/5-workshop/5.9.4-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.sepay.vn/>
