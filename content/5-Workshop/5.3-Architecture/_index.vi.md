---
title: "Kiến trúc và luồng dữ liệu"
weight: 3
chapter: false
pre: "<b> 5.3. </b> "
---

# 5.3. Kiến trúc production và luồng dữ liệu

Dùng **AWS Architecture Diagram do nhóm tự vẽ/kiểm tra bằng draw.io với AWS 2026 Icons**. Chỉ đưa PNG cuối khi đã đối chiếu topology đang chạy. Không ghi CIDR, Region, 2 AZ hoặc NAT là dữ liệu thật nếu AWS Console chưa xác nhận.

**File ảnh dự kiến:** `static/images/5-workshop/architecture/btb-production-reviewed.png`.

## Kiến trúc logic (chưa xác minh subnet thực tế)

```text
Người dùng (Guest / Customer / Staff / Admin)
  |-- domain FE (Route 53) --> CloudFront + WAF frontend --> S3 React build
  |       |-- HTTPS cert: ACM (CloudFront dùng cert tại us-east-1)
  |       `-- RUM client -> Cognito Identity Pool -> CloudWatch RUM
  `-- domain API (Route 53) --> ALB + WAF regional BE [rule giới hạn: COUNT]
                                    --> ECS Fargate (Spring Boot trong VPC)
                                          |-- ECR image, Secrets Manager, IAM
                                          |-- Supabase PostgreSQL / Auth được nhóm báo cáo
                                          |-- Bedrock [endpoint production chưa xác minh]
                                          |-- Cloudinary ảnh
                                          |-- Vietmap bản đồ/địa chỉ
                                          |-- SePay QR & webhook xác thực
                                          `-- Gmail SMTP gửi OTP

CloudWatch Logs + Metrics/Alarms -> SNS -> email vận hành
AWS Budgets -> email cảnh báo chi phí
GitHub `feat/prod` -> Actions -> ECR/ECS (BE); S3/CloudFront (FE)
```

## Giải thích các luồng

1. **Frontend:** Browser tra DNS, TLS với CloudFront và tải SPA; S3 là origin, không phải trang HTTPS công khai chính.
2. **API:** Browser tra DNS API và kết nối HTTPS đến ALB; WAF regional được **associate** với ALB, không phải proxy đứng riêng; ALB forward task ECS.
3. **Webhook thanh toán:** SePay gửi callback vào backend; backend kiểm tra xác thực, event id và thanh toán trước khi cập nhật Order.
4. **Email ứng dụng:** Spring Boot dùng Gmail SMTP gửi OTP; SNS gửi email CloudWatch Alarm chứ không gửi OTP.
5. **Monitoring:** ECS logs đến CloudWatch Logs; metrics tới alarms/SNS; browser RUM dùng credential giới hạn qua Cognito Identity Pools.
6. **CI/CD:** GitHub Actions trên `feat/prod` build/deploy FE lên S3/CloudFront và BE lên ECR/ECS.

## Checklist sơ đồ trước khi nộp

- [ ] CloudFront, Route 53, SNS không nằm trong một subnet riêng của VPC.
- [ ] Phân biệt resource Region và global; cert CloudFront ở us-east-1.
- [ ] Subnet/AZ, NAT/egress và IAM giống AWS Console.
- [ ] Có WAF FE/BE, ghi rule BE là **Count**, chưa block.
- [ ] Supabase, Cloudinary, Vietmap, SePay, Gmail SMTP ở ngoài AWS Cloud.
- [ ] Bedrock/RUM ghi **cần kiểm chứng** nếu chưa test production.

Các bài 5.4–5.10 giải thích chi tiết. Không đăng sơ đồ có IP/CIDR hoặc resource tự đoán.
