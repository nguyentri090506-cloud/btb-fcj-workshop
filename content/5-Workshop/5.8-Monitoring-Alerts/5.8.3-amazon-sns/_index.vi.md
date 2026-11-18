---
title: "Amazon SNS"
weight: 3
chapter: false
pre: "<b> 5.8.3. </b> "
---

# 5.8.3. Amazon SNS

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã cấu hình subscription email.

## Mục tiêu và vai trò trong hệ thống

Gửi email cảnh báo alarm đến email subscriber đã xác nhận.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở SNS → Topics, tìm topic gắn alarm CloudWatch production và ghi ARN (không kèm credential).
2. Mở Subscriptions, xác nhận `Protocol = Email`, email đích và trạng thái `Confirmed`, không phải PendingConfirmation.
3. Đối chiếu action của CloudWatch Alarm đang publish đúng SNS topic.
4. Kiểm tra inbox/spam tìm email alarm đã có hoặc kiểm thử có phê duyệt của nhóm.
5. Lưu timestamp, subject và vai trò email nhận; che địa chỉ theo chính sách nếu cần.
6. Phân biệt email cảnh báo hạ tầng SNS với email OTP khách hàng gửi bằng Gmail SMTP.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Subscription đã xác nhận, alarm trỏ đúng topic và có minh chứng email nếu từng được gửi.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Có subscription SNS không đồng nghĩa alarm đã thực sự kích hoạt.

## Ảnh minh chứng cần chụp

SNS topic/subscription (che email) và thư cảnh báo nếu đã có.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.8.3-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/sns/latest/dg/sns-email-notifications.html>
