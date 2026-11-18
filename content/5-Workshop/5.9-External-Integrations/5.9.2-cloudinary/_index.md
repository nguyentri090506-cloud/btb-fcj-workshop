---
title: "Cloudinary Media"
weight: 2
chapter: false
pre: "<b> 5.9.2. </b> "
---

# 5.9.2. Cloudinary Media

> **Source status, as reported by the BTB team (18 November 2026):** External provider identified for product/media including avatars.

## Objective and actual role

Serves BTB product, content and avatar images independently of the S3 frontend build.

## Lab: inspect, document and verify the existing production setup

1. Inspect the existing Cloudinary project/folder structure; record only public asset references, not API secrets.
2. Open the deployed React frontend and confirm product card/brand/avatar image URLs resolve through the intended Cloudinary CDN.
3. For a controlled upload example, use a test-only account/image and follow the backend-approved signed or server-side upload flow, not an unrestricted unsigned upload endpoint.
4. Validate allowed image formats, size limits and authenticated ownership where images represent Customer data.
5. Inspect broken image behavior and ensure the backend stores public_id/secure_url references consistently for the feature.
6. Document S3/frontend vs Cloudinary/image responsibilities so they are not conflated in the AWS diagram.

## Expected outcome / result recording

**Expected:** Public intended images load; test upload follows authorization rules; Cloudinary credentials stay private.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Cloudinary URL/public_id naming may differ by project; avoid fabricating folder names.

## Screenshot evidence to capture

Image URL on page, allowed asset metadata, redacted upload confirmation.

**Suggested path:** `static/images/5-workshop/5.9.2-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://cloudinary.com/documentation/image_upload_api_reference>
