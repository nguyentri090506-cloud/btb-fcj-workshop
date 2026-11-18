---
title: "Amazon ECR"
weight: 1
chapter: false
pre: "<b> 5.5.1. </b> "
---

# 5.5.1. Amazon ECR

> **Source status, as reported by the BTB team (18 November 2026):** Used in current CI/CD.

## Objective and actual role

Private repository containing the Docker image consumed by ECS Fargate.

## Lab: inspect, document and verify the existing production setup

1. Open ECR → Private repositories; find the repository used by BTB backend and record actual name, Region, encryption setting and tag strategy.
2. Inspect images and note the deployed immutable digest/tag, upload time and image size; never guess an existing version.
3. Check GitHub Actions authentication, image build and push steps; use short-lived role credentials where configured.
4. Open ECS task definition and compare the image URI/digest with ECR; confirm that the version ECS actually runs is the expected release.
5. Review repository scanning and image lifecycle policy; coordinate pruning old images to avoid deleting a rollback target.
6. Record evidence of successful image publication and ECS deployment from the production pipeline.

## Expected outcome / result recording

**Expected:** Actual image digest referenced by the running task matches ECR image metadata.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

A tag such as `latest` alone is insufficient release traceability; prefer immutable SHA/digest.

## Screenshot evidence to capture

Repository image list, digest and task definition image URI.

**Suggested path:** `static/images/5-workshop/5.5.1-01.png` (capture from real Console; do not create a fake screenshot).

## Optional read-only command

```powershell
# Illustrative only: replace placeholders and ensure AWS CLI auth is configured
aws ecr describe-images --repository-name <ECR_REPOSITORY> --region <AWS_REGION>
```

## Official reference

<https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html>
