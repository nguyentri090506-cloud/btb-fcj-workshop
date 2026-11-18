---
title: "Dự toán chi phí"
weight: 12
chapter: false
pre: "<b> 5.12. </b> "
---

# 5.12. Dự toán và tối ưu chi phí

Dùng **[AWS Pricing Calculator](https://calculator.aws/)** với Region và thông số runtime thật. **Không tự bịa bill tháng.** Ngưỡng AWS Budgets, chi phí AWS thực tế và dự toán Calculator là 3 dữ liệu khác nhau.

## Các đầu vào cần đo

| Dịch vụ | Yếu tố tạo chi phí | Thực tế |
|---|---|---|
| ECS Fargate | số task, vCPU, RAM GiB, giờ chạy | TODO |
| ALB | số giờ, LCU, lưu lượng | TODO |
| ECR | dung lượng image, scanning, lifecycle | TODO |
| S3 | GB/tháng, requests, versioning | TODO |
| CloudFront | GB outbound theo vùng, requests, invalidation | TODO |
| Route 53 + ACM | hosted zone, DNS queries, loại chứng chỉ | TODO |
| Secrets Manager | số secret/tháng và API calls | TODO |
| CloudWatch Logs/Metrics/Alarms | ingest, retention, custom metrics, alarms | TODO |
| SNS | số notification | TODO |
| CloudWatch RUM | sự kiện trình duyệt/retention | TODO |
| Cognito Identity Pools | cơ chế cấp credential; đối chiếu khoản phí | TODO |
| WAF | Web ACL, rule, managed groups, requests | TODO |
| Bedrock | số token/giá model, cách inference, Region | TODO |
| VPC | public IPv4, data egress, NAT/endpoints nếu thực có | TODO |
| Budgets | chi phí budget/notification áp dụng | TODO |
| Dịch vụ ngoài AWS | Supabase, Cloudinary, Vietmap, SePay, Gmail SMTP | TODO (riêng) |

## Hướng tối ưu

1. Dựa trên CPU/RAM ECS và ALB metrics trước khi giảm resource; nếu 1 task/1 AZ phải ghi giới hạn HA.
2. Cache asset frontend phù hợp; xem CloudFront data transfer.
3. Cấu hình retention log, lifecycle ECR và xóa version S3 có kiểm soát.
4. Đọc sampled requests WAF trước khi chuyển rule BE từ Count sang Block.
5. Theo dõi token Bedrock và sampling/ingest RUM; không mặc định miễn phí.
6. Chụp/export Calculator có ngày, ghi assumptions và đối chiếu với Budgets thực tế.

**Bài nộp:** link/export Calculator, giả định, bảng từng dịch vụ và phân tích tối ưu. Chưa đủ input thì không đưa số tổng giả.
