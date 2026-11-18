---
title: "Amazon CloudWatch Logs"
weight: 1
chapter: false
pre: "<b> 5.8.1. </b> "
---

# 5.8.1. Amazon CloudWatch Logs

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Log BE đã cấu hình.

## Mục tiêu và vai trò trong hệ thống

Log stdout/stderr của Spring Boot để phân tích startup, lỗi API/tích hợp.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở CloudWatch → Logs → Log groups, tìm group đúng theo `awslogs` trong ECS task definition.
2. Xem log streams của task ECS đang chạy, đối chiếu timestamp với bản deploy gần nhất.
3. Gọi GET API an toàn và quan sát log/trace tương ứng nếu ứng dụng có log sự kiện đó.
4. Lọc WARN/ERROR để phân biệt lỗi DB, Bedrock, SePay webhook hoặc SMTP; che dữ liệu cá nhân.
5. Kiểm tra retention và chi phí ingest; sửa retention chỉ khi được nhóm đồng ý.
6. Chụp log group/stream và một dòng log liên quan đã che token, email, mật khẩu, connection string.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Log bám đúng task đang chạy, hỗ trợ debug và không lộ bí mật.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

CloudWatch Logs không thay thế audit nghiệp vụ (ai duyệt Quote, chỉnh giá, v.v.).

## Ảnh minh chứng cần chụp

Cấu hình awslogs, log streams và log sức khỏe/lỗi đã che dữ liệu.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.8.1-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html>
