---
title: "CI/CD Deployment"
weight: 10
chapter: false
pre: "<b> 5.10. </b> "
---

# 5.10. GitHub Actions CI/CD from `feat/prod`

The team reports automatic frontend/backend deployment from the application repository's `feat/prod` branch. **This is different from the `docs/...` branch used for the FCAJ Hugo Workshop repository.** Use the actual existing workflow files as authoritative configuration; the actions below are verification steps and do not claim a new pipeline was created.

## 5.10.1. Frontend — React → S3 → CloudFront

1. Open the FE repository → `.github/workflows/` and identify the production workflow trigger for `feat/prod`.
2. Inspect `npm ci`, tests (if present), production build and environment configuration; never put backend secrets into Vite `VITE_*` variables (they are exposed to the browser).
3. Inspect AWS deploy authentication (prefer OIDC), S3 bucket sync target and CloudFront invalidation path; capture the most recent successful run ID and commit SHA.
4. Open the live frontend and check a new non-sensitive release marker or static asset hash; verify cache invalidation did not mask old assets.
5. Describe rollback to a known previous build artifact/commit; do not force a production rollback for a screenshot.

## 5.10.2. Backend — Spring Boot → Docker → ECR → ECS

1. Open the BE repo's production workflow and check its `feat/prod` trigger and protected deployment environment.
2. Inspect the build/test phase, Docker build, image tag/digest and the role assumed by GitHub Actions.
3. Confirm the push target ECR repository and the ECS task-definition/service update operation.
4. Compare latest successful workflow SHA to ECR digest, ECS deployment event and running task definition; check ALB healthy targets.
5. Record rollback strategy, readiness checks and safe failure handling.

### Example source-only checks (do not deploy)

```powershell
git branch -a
git log -5 --oneline
git remote -v
```

**Evidence:** FE/BE Actions run URLs, trigger config, commit SHA, ECR digest, ECS service task, S3 build output and CloudFront distribution.
