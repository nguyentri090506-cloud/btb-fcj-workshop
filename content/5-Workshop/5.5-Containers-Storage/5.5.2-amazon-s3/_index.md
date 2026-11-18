---
title: "Amazon S3"
weight: 2
chapter: false
pre: "<b> 5.5.2. </b> "
---

# 5.5.2. Amazon S3

> **Source status, as reported by the BTB team (18 November 2026):** Production frontend files stored.

## Objective and actual role

Stores static compiled frontend files; product and avatar media use Cloudinary instead.

## Lab: inspect, document and verify the existing production setup

1. Open S3 → Buckets and identify the bucket containing the deployed React `dist/` or build artifacts.
2. Check object keys, `index.html`, JS/CSS assets, cache-control metadata, bucket Region, public-access settings and bucket policy.
3. Inspect the CloudFront origin; if the bucket is private, verify Origin Access Control (OAC) and matching bucket policy.
4. Confirm the frontend pipeline syncs the intended local build directory and does not remove unrelated objects without review.
5. When deploying a new SPA version, invalidate the appropriate CloudFront paths and check the page loads refreshed asset hashes.
6. Do not use this bucket as the default storage for Cloudinary-managed product images and avatars.

## Expected outcome / result recording

**Expected:** CloudFront loads built assets, S3 direct public access is disabled if OAC is used, and SPA refresh works for configured routes.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

If the team deliberately uses another S3 origin policy, describe what is actually configured instead of silently claiming OAC.

## Screenshot evidence to capture

Bucket objects/permissions, CloudFront origin and browser successful load.

**Suggested path:** `static/images/5-workshop/5.5.2-01.png` (capture from real Console; do not create a fake screenshot).

## Optional read-only command

```powershell
# Local sanity check of build folder (choose dist or build as your project uses)
Get-ChildItem .\dist -ErrorAction SilentlyContinue
```

## Official reference

<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html>
