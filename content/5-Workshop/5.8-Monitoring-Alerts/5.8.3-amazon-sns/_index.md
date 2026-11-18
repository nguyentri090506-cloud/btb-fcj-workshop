---
title: "Amazon SNS"
weight: 3
chapter: false
pre: "<b> 5.8.3. </b> "
---

# 5.8.3. Amazon SNS

> **Source status, as reported by the BTB team (18 November 2026):** Email subscription configured.

## Objective and actual role

Sends alarm notifications to verified email subscriptions.

## Lab: inspect, document and verify the existing production setup

1. Open SNS → Topics; find the topic connected to the production CloudWatch alarm and record the topic ARN without credentials.
2. Open Subscriptions and verify `Protocol = Email`, the intended endpoint, and `Confirmed` status rather than PendingConfirmation.
3. Inspect the CloudWatch alarm action; confirm it publishes to this SNS topic, not another test topic.
4. Check mailbox and spam folder for a real historical alarm message or a controlled team-approved test event.
5. Document delivery timestamp, alert subject and recipient role with email addresses redacted as appropriate.
6. Explain SNS messages for infrastructure alerts are separate from BTB customer OTP emails handled by Gmail SMTP.

## Expected outcome / result recording

**Expected:** Confirmed subscription exists, alarm action points to topic and observed alert email is documented if available.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

SNS subscriptions alone do not guarantee an alarm fired.

## Screenshot evidence to capture

SNS topic/subscription (redacted) and actual alert email if available.

**Suggested path:** `static/images/5-workshop/5.8.3-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/sns/latest/dg/sns-email-notifications.html>
