---
title: "Triển khai Backend và AI"
weight: 6
chapter: false
pre: "<b> 5.6. </b> "
---

# 5.6. Triển khai Backend và AI

Giai đoạn này ghi cấu hình BTB theo báo cáo của nhóm. Xem từng bài lab, bổ sung kết quả và ảnh chụp resource thật.

- [5.6.1. AWS Secrets Manager](5.6.1-aws-secrets-manager/) — Lưu cấu hình nhạy cảm của BE: database, AI, webhook, mail.
- [5.6.2. Application Load Balancer](5.6.2-application-load-balancer/) — Điểm vào API HTTPS, chuyển request về ECS target khỏe.
- [5.6.3. Amazon ECS kết hợp AWS Fargate](5.6.3-amazon-ecs-fargate/) — Chạy API Spring Boot modular monolith qua container managed.
- [5.6.4. Amazon Bedrock](5.6.4-amazon-bedrock/) — Cung cấp AI model inference cho backend/Generate UI; quyền nghiệp vụ vẫn do Spring Boot kiểm soát.
