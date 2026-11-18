---
title: "Application Load Balancer"
weight: 2
chapter: false
pre: "<b> 5.6.2. </b> "
---

# 5.6.2. Application Load Balancer

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã hoạt động production.

## Mục tiêu và vai trò trong hệ thống

Điểm vào API HTTPS, chuyển request về ECS target khỏe.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở EC2 → Load Balancers, ghi tên ALB production, scheme và VPC thực tế.
2. Kiểm tra listener/port, chứng chỉ ACM cho HTTPS 443 và rule HTTP→HTTPS nếu có.
3. Vào Target groups, xác nhận target type **IP** với Fargate awsvpc, protocol/port, health check path và success code thực tế.
4. Xem target đã register, trạng thái healthy/unhealthy; ghi lý do lỗi nếu có, không đoán.
5. Kiểm tra SG ALB inbound và SG ECS chỉ nhận backend port từ ALB SG, không public trực tiếp.
6. Dùng API domain thực tế gọi endpoint GET an toàn; lưu HTTP status, TLS và bằng chứng routing.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Listener HTTPS đúng, target healthy trùng ECS và API trả response qua ALB.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Với API trực tiếp qua ALB, WAF trên CloudFront không bảo vệ API; cần Web ACL regional riêng.

## Ảnh minh chứng cần chụp

Listener, target health, target type IP và response API an toàn.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.6.2-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonECS/latest/developerguide/alb.html>
