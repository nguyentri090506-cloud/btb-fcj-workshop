---
title: "CloudWatch RUM"
weight: 4
chapter: false
pre: "<b> 5.8.4. </b> "
---

# 5.8.4. CloudWatch RUM

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã tạo monitor, thêm code FE; còn phải xác nhận có dữ liệu thực tế.

## Mục tiêu và vai trò trong hệ thống

Theo dõi hiệu năng và lỗi JavaScript của frontend React từ trình duyệt.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Vào CloudWatch → RUM/Application Signals, xác định app monitor production, Region và domain được theo dõi.
2. Kiểm tra monitor: origin/domain hợp lệ, loại telemetry, sample rate và cấu hình lưu dữ liệu.
3. Kiểm tra bản frontend React đã deploy thật có khởi tạo RUM client/snippet, không chỉ ở branch local.
4. Đối chiếu Cognito Identity Pool SDK dùng, mở DevTools Network/Console tìm request telemetry bị chặn hoặc lỗi CORS.
5. Truy cập website thật theo policy consent/privacy, chuyển một số trang không nhạy cảm rồi kiểm tra RUM page views/performance/errors.
6. Nếu chưa có dữ liệu, ghi `Chưa xác minh`, timestamp kiểm tra và nguyên nhân nghi ngờ; không ghi chạy thành công chỉ vì monitor đã tạo.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** RUM có page views/errors từ domain thật; chưa thấy thì để pending.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

RUM có thể thu URL/metadata trình duyệt; kiểm tra chính sách dữ liệu cá nhân và consent.

## Ảnh minh chứng cần chụp

App monitor, vị trí SDK trong FE, request đã che dữ liệu và RUM dashboard.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.8.4-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-RUM-get-started.html>
