---
title: "Triển khai CI/CD"
weight: 10
chapter: false
pre: "<b> 5.10. </b> "
---

# 5.10. GitHub Actions CI/CD từ `feat/prod`

Nhóm báo cáo FE/BE deploy tự động qua GitHub Actions từ branch **`feat/prod`** của repo ứng dụng. **Branch này khác `docs/...` dùng viết báo cáo Hugo FCAJ.** Nội dung dưới là bước **kiểm tra workflow đang tồn tại**, không khẳng định nhóm tạo pipeline mới.

## 5.10.1. Frontend — React → S3 → CloudFront

1. Vào repo FE → `.github/workflows/`, xác định workflow production trigger `feat/prod`.
2. Kiểm tra `npm ci`, test nếu có, production build và môi trường; không đặt secret backend trong `VITE_*` vì biến này bị đưa ra browser.
3. Kiểm tra xác thực AWS (ưu tiên OIDC), đường dẫn sync S3 và CloudFront invalidation; ghi run ID và commit SHA gần nhất thành công.
4. Mở FE production, đối chiếu asset hash/bản release an toàn; kiểm tra invalidation không còn cache cũ.
5. Ghi phương án rollback về build/commit cũ; không rollback production chỉ để chụp hình.

## 5.10.2. Backend — Spring Boot → Docker → ECR → ECS

1. Mở repo BE workflow production, kiểm tra trigger `feat/prod` và deployment environment.
2. Xem build/test, Docker image tag/digest và role GitHub Actions assume.
3. Xác minh repository ECR nhận image và lệnh cập nhật task definition/service ECS.
4. Đối chiếu commit SHA thành công với ECR digest, ECS task definition và ALB healthy targets.
5. Ghi rollback và cách xử lý build/test/deploy lỗi.

### Lệnh kiểm tra source code, không deploy

```powershell
git branch -a
git log -5 --oneline
git remote -v
```

**Minh chứng:** URL Actions run FE/BE, trigger config, SHA commit, digest ECR, task ECS, object S3 và CloudFront distribution.
