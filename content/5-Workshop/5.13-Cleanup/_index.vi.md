---
title: "Dọn tài nguyên và khắc phục lỗi"
weight: 13
chapter: false
pre: "<b> 5.13. </b> "
---

# 5.13. Dọn tài nguyên và xử lý lỗi

## Không được xóa production để hoàn thành workshop

**Không xóa/tắt hạ tầng production đang chạy chỉ để chụp Cleanup.** Phần này chỉ dành cho **tài nguyên lab riêng** khi được phép. Giữ nguyên VPC, ECS, ALB, Route 53, CloudFront, S3, ECR, WAF, Secrets Manager, IAM, Budgets, RUM, Cognito, Bedrock và monitoring chung của nhóm.

## Thứ tự cleanup cho môi trường lab riêng

1. Lưu ảnh test đã che dữ liệu, ghi resource ID và chi phí cần đối chiếu.
2. Tắt/xóa ECS service/task lab sau khi được duyệt; xóa listener/target group và ALB lab tương ứng.
3. Gỡ WAF lab khỏi CloudFront, disable distribution và xóa khi AWS cho phép.
4. Dọn object và version ở bucket **riêng của lab** rồi xóa bucket nếu không còn dùng.
5. Xóa image/repository ECR lab và secret lab không còn tham chiếu (Secrets Manager có recovery window).
6. Chỉ xóa IAM role, log group, SNS topic, alarm, RUM monitor/Cognito pool, record Route 53 test khi xác nhận không dùng chung.
7. Kiểm tra phí còn lại, domain registration và subscription ngoài AWS; billing có độ trễ.

## Các lỗi thường gặp

| Hiện tượng | Kiểm tra trước |
|---|---|
| Web 403/404 khi refresh route | CloudFront origin/OAC và SPA fallback |
| API 502/503 | ALB target health, ECS port/SG, task logs |
| ECS `CannotPullContainerError` | ECR URI, execution role, outbound network |
| BE không kết nối Supabase | TLS/DNS, egress, secret, pool |
| Bedrock AccessDenied | Region/model, task role, model profile |
| WAF có match nhưng request vẫn qua | Rule có thể **Count**, không Block |
| CloudWatch Alarm không gửi email | alarm action, SNS topic/subscription Confirmed |
| RUM không nhận dữ liệu | FE code deploy, domain, Cognito role, browser telemetry |
| SePay callback lỗi | HTTPS route, auth theo provider, idempotency, logs |
| Gmail OTP không đến | SMTP/TLS/credentials, recipient, rate limit |
| Hugo local lỗi | Hugo version/theme và shortcode `getJSON` cũ |

## Checklist hoàn thiện

- [ ] Mỗi dịch vụ có ảnh và resource ID đã đối chiếu.
- [ ] Có kết quả test thật, kể cả lỗi chưa sửa.
- [ ] Sơ đồ draw.io được nhóm kiểm tra và xuất ảnh có ngày.
- [ ] Có Pricing Calculator và Live Demo.
- [ ] GitHub không chứa secret hoặc PII Customer.
