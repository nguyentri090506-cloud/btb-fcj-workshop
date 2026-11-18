---
title: "Amazon ECS kết hợp AWS Fargate"
weight: 3
chapter: false
pre: "<b> 5.6.3. </b> "
---

# 5.6.3. Amazon ECS kết hợp AWS Fargate

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Backend đã chạy production.

## Mục tiêu và vai trò trong hệ thống

Chạy API Spring Boot modular monolith qua container managed.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở ECS → Clusters → service BTB; ghi desired/running/pending tasks và trạng thái deployment thực tế.
2. Ở task definition revision, ghi image URI, cổng, CPU/RAM, Fargate platform, execution role, task role và logging.
3. Kiểm tra subnet/SG/public IP của task và target group ALB gắn với ECS.
4. Đọc ECS deployment events, task health; so image digest với ECR và xác nhận log stream có trên CloudWatch Logs.
5. Test API production an toàn (GET catalog hoặc auth bằng tài khoản test), không tạo đơn thật hoặc lộ dữ liệu khách.
6. Mô tả rollback về task revision/image digest **đã kiểm chứng**, update service và theo dõi target healthy; không rollback thật chỉ để minh họa.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Số running task đáp ứng desired, ALB có target healthy và CloudWatch có log tương ứng.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Chạy 1 task/1 AZ có thể là cấu hình tiết kiệm nhưng không được gọi là high availability.

## Ảnh minh chứng cần chụp

ECS service, task đang chạy, task definition, service events.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.6.3-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Lệnh kiểm tra tham khảo (read-only)

```powershell
# CLI read-only example; replace placeholders
aws ecs describe-services --cluster <CLUSTER> --services <SERVICE> --region <AWS_REGION>
```

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonECS/latest/developerguide/what-is-fargate.html>
