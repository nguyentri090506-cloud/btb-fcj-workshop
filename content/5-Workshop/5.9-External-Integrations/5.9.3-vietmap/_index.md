---
title: "Vietmap Maps & Location"
weight: 3
chapter: false
pre: "<b> 5.9.3. </b> "
---

# 5.9.3. Vietmap Maps & Location

> **Source status, as reported by the BTB team (18 November 2026):** External provider listed; exact production API paths/keys must be verified.

## Objective and actual role

Map, address lookup and distance display for BTB deliveries.

## Lab: inspect, document and verify the existing production setup

1. Find the deployed Customer/Delivery Staff screens that render Vietmap and confirm the map tiles/markers load over HTTPS.
2. Verify configured API keys and allowed origins/restrictions without exposing them publicly in screenshots.
3. Use a test delivery destination and inspect address search/geocoding and displayed route/distance results.
4. Describe the current BTB demo business assumption: one warehouse, multiple order packages/delivery points, and illustrative ETA based on 40 km/h, not guaranteed road time.
5. Check how the frontend/backend handles Vietmap timeout, quota errors and denied requests; document fallback text rather than silent failures.
6. Capture anonymized map evidence and avoid displaying real Customer street addresses.

## Expected outcome / result recording

**Expected:** Map, location and distance feature produces test-only results consistent with documented demo assumptions.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

ETA is illustrative; it is not a live GPS, traffic-aware ETA or a guarantee.

## Screenshot evidence to capture

Test route and location screen with anonymized destinations.

**Suggested path:** `static/images/5-workshop/5.9.3-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://maps.vietmap.vn/>
