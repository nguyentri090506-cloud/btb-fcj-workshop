---
title: "Amazon ECR"
weight: 1
chapter: false
pre: "<b> 5.5.1. </b> "
---

# 5.5.1. Amazon ECR

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đang dùng trong CI/CD.

## Mục tiêu và vai trò trong hệ thống

Kho Docker image backend để ECS Fargate kéo về chạy.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở ECR → Private repositories, xác định repository backend BTB; ghi tên, Region, mã hóa và chiến lược tag thực tế.
2. Xem Images, ghi digest/tag, thời điểm push và dung lượng của phiên bản đang deploy; không tự đoán số version.
3. Kiểm tra các bước xác thực, Docker build, push trong GitHub Actions; ưu tiên role ngắn hạn nếu đang cấu hình.
4. Mở ECS task definition, đối chiếu image URI/digest với ECR; xác nhận đúng bản release chạy thật.
5. Xem scanning và lifecycle policy; trao đổi trước khi xóa các image cũ để vẫn rollback được.
6. Lưu bằng chứng push image thành công và ECS triển khai từ pipeline production.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Image digest của ECS đang chạy khớp image trong ECR.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Tag `latest` không đủ truy vết release; nên lưu SHA/digest cố định.

## Ảnh minh chứng cần chụp

Danh sách image ECR, digest và image URI ở ECS task definition.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.5.1-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Lệnh kiểm tra tham khảo (read-only)

```powershell
# Illustrative only: replace placeholders and ensure AWS CLI auth is configured
aws ecr describe-images --repository-name <ECR_REPOSITORY> --region <AWS_REGION>
```

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html>
