---
title: "Workshop"
weight: 5
chapter: false
pre: "<b> 5. </b> "
---

# Triển khai Bite to Business trên AWS — Workshop toàn hệ thống

Workshop trình bày **kiến trúc production do nhóm báo cáo** và hướng dẫn đối chiếu, xác minh, xử lý lỗi và viết minh chứng. Bản này bao gồm **toàn bộ dịch vụ của cả nhóm**, không còn chỉ phần riêng một thành viên. **Bite to Business (BTB)** là website bán thực phẩm trực tiếp, ưu tiên khách doanh nghiệp nhưng vẫn hỗ trợ cá nhân/hộ gia đình; **không phải marketplace nhiều người bán**.

Frontend React/TypeScript được triển khai qua **S3 → CloudFront**, kết hợp **Route 53, ACM và WAF**. Backend Java Spring Boot modular monolith chạy **ECS + Fargate** sau **Application Load Balancer**, Docker image lưu **ECR**. Nhóm dùng **IAM, Secrets Manager, CloudWatch Logs/Metrics/Alarms, SNS, Budgets, CloudWatch RUM và Cognito Identity Pools**, cùng **Amazon Bedrock** cho mô hình AI. **Supabase, Cloudinary, Vietmap, SePay và Gmail SMTP** là dịch vụ ngoài AWS. **GitHub Actions** deploy FE/BE từ `feat/prod`.

**Giới hạn minh chứng:** trạng thái được tổng hợp từ bảng nhóm gửi ngày **18/11/2026**, chưa phải kết quả truy cập AWS Console trực tiếp. API Bedrock production và dữ liệu RUM **cần kiểm chứng**; rule giới hạn WAF backend là **Count**, chưa chặn. Tài liệu nghiệp vụ cũ còn nhắc Gemini và mâu thuẫn về Supabase Auth/JWT nên phải đối chiếu code production trước khi chốt.

**Không tự đưa vào production:** SQS, SES, CodePipeline/CodeBuild, CloudTrail, NAT Gateway và VPC endpoints từng nằm trong các kế hoạch cũ nhưng **không có trong danh sách production cập nhật**. Không mô tả chúng như đã chạy.

## Mục lục

- [5.1. Tổng quan](5.1-overview/)
- [5.2. Chuẩn bị](5.2-prerequisites/)
- [5.3. Kiến trúc và luồng dữ liệu](5.3-architecture/)
- [5.4. Mạng và thiết lập nền tảng](5.4-foundation/)
- [5.5. Container và lưu trữ](5.5-containers-storage/)
- [5.6. Triển khai Backend và AI](5.6-backend-ai/)
- [5.7. Phân phối web và bảo mật](5.7-web-security/)
- [5.8. Giám sát và cảnh báo](5.8-monitoring-alerts/)
- [5.9. Tích hợp dịch vụ bên ngoài](5.9-external-integrations/)
- [5.10. Triển khai CI/CD](5.10-ci-cd/)
- [5.11. Kiểm thử và trình diễn](5.11-testing/)
- [5.12. Dự toán chi phí](5.12-cost/)
- [5.13. Dọn tài nguyên và khắc phục lỗi](5.13-cleanup/)

## Quy tắc ghi minh chứng

Mỗi bài có tình trạng nhóm báo, các bước thao tác/đối chiếu, kết quả mong đợi, ô để điền kết quả thực và vị trí gợi ý chụp màn hình. **Phải thay placeholder bằng ảnh AWS Console có ngày giờ**, log CI/CD và bài test đã che dữ liệu. Không trình bày ví dụ thành kết quả đã kiểm thử. Không đưa secret hay hồ sơ Customer lên GitHub.
