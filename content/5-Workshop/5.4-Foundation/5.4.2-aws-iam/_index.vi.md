---
title: "AWS IAM"
weight: 2
chapter: false
pre: "<b> 5.4.2. </b> "
---

# 5.4.2. AWS IAM

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã có role; cần đối chiếu trust policy và quyền tối thiểu.

## Mục tiêu và vai trò trong hệ thống

Phân quyền cho ECS task execution, backend gọi Bedrock và GitHub Actions deploy.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở IAM → Roles; xác định tên thực tế của ECS task execution role, task role và CI/CD deployment role.
2. Đối chiếu execution role: pull image ECR, ghi CloudWatch Logs và lấy secret được tham chiếu trong task definition.
3. Kiểm tra task role của ứng dụng riêng biệt; xác nhận quyền Bedrock/model chỉ đủ cho backend.
4. Nếu GitHub Actions dùng OIDC, kiểm tra provider và trust policy; giới hạn `sub` theo repo và branch `feat/prod` dự kiến.
5. Xem JSON policy và lịch sử dùng nếu có; chỉ điều chỉnh quyền rộng sau khi đã trao đổi nhóm.
6. Ghi chức năng từng role; IAM của AWS không thay thế phân quyền Guest/Customer/Staff của BTB.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Role và trust relationship được tách đúng; quyền Bedrock đủ dùng; không commit access key dài hạn cho CI/CD.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Không đăng access key, token phiên hoặc khóa bí mật lên workshop.

## Ảnh minh chứng cần chụp

Tên role, tóm tắt trust policy, policy gắn kèm (che nội dung nhạy cảm).

**Đường dẫn gợi ý:** `static/images/5-workshop/5.4.2-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html>
