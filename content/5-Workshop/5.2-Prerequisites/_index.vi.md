---
title: "Chuẩn bị"
weight: 2
chapter: false
pre: "<b> 5.2. </b> "
---

# 5.2. Chuẩn bị

**Workshop này ưu tiên kiểm tra/xác minh hệ thống production đã có.** Không tự tạo trùng tài nguyên đang chạy. Thí nghiệm thay đổi/xóa cấu hình chỉ làm ở môi trường lab riêng có phép.

## Quyền truy cập và công cụ

1. AWS account có quyền đọc VPC, ECS, ECR, S3, ALB, ACM, Route 53, WAF, CloudWatch, SNS, RUM, Cognito, IAM, Secrets Manager và Bedrock. Xin role ít quyền; sửa production phải được phê duyệt.
2. Truy cập GitHub repo FE/BE và Actions branch `feat/prod`; Docker, Java/Spring Boot, Node/npm, PowerShell, `git`, AWS CLI và `curl` (nếu cần).
3. Có FE/API domain thật, AWS Region, ECS cluster/service, ECR repo, S3 bucket, CloudFront distribution, ALB target group, SNS topic và RUM monitor.
4. Dùng tài khoản Customer/Staff/Admin thử và dữ liệu demo; không đưa thông tin khách thật hoặc giao dịch thật lên workshop.
5. Ảnh minh chứng cần thể hiện cấu hình/kết quả; che ARN/account nếu policy yêu cầu và **luôn che secret**.

## Bảng thông số cần điền trước

| Biến | Ví dụ / yêu cầu | Giá trị thực |
|---|---|---|
| `AWS_REGION` | Region đang chạy BE | TODO |
| `FRONTEND_DOMAIN` | Domain frontend HTTPS | TODO |
| `API_DOMAIN` | Hostname API HTTPS | TODO |
| `ECS_CLUSTER`, `ECS_SERVICE` | Tên ECS production | TODO |
| `ECR_REPOSITORY`, `S3_BUCKET` | Repo image/bucket frontend | TODO |
| `BEDROCK_MODEL_ID` | Model/inference profile thật | TODO |
| `RUM_MONITOR`, `SNS_TOPIC` | Resource monitoring thật | TODO |

## Bảo đảm an toàn

Xin phép trước khi đổi WAF, IAM, SG, ECS, DB, webhook hoặc DNS. Ưu tiên thao tác đọc. Lưu ảnh vào `static/images/5-workshop/`, không đính kèm credential.
