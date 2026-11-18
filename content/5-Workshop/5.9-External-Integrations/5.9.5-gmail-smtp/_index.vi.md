---
title: "Gmail SMTP gửi OTP hệ thống"
weight: 5
chapter: false
pre: "<b> 5.9.5. </b> "
---

# 5.9.5. Gmail SMTP gửi OTP hệ thống

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Nhóm báo dùng Gmail SMTP; cần test OTP thật, tách với email cảnh báo SNS.

## Mục tiêu và vai trò trong hệ thống

Gửi email hệ thống BTB như OTP kích hoạt và đặt lại mật khẩu.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Kiểm tra SMTP host, port, STARTTLS, email người gửi và nơi lấy credential trong backend, không in password/app password.
2. Đảm bảo secret SMTP đặt ở Secrets Manager hoặc nơi được phê duyệt, ECS task lấy an toàn.
3. Dùng Gmail test, thực hiện flow thực tế: Admin duyệt → gửi OTP → Customer nhập OTP → kích hoạt/đặt lại password theo code hiện tại.
4. Xác nhận email đến, OTP một lần/hết hạn, rate limit và log backend không ghi OTP thô.
5. Test OTP sai/hết hạn bằng tài khoản thử để xác nhận bị từ chối và không lộ thông tin.
6. Phân biệt Gmail SMTP gửi OTP ứng dụng với SNS gửi email CloudWatch Alarm.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Inbox test nhận OTP đúng luồng, OTP sai/hết hạn bị từ chối và bí mật không bị lộ.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Không đưa OTP thật, mật khẩu Gmail hoặc SMTP credential vào GitHub public.

## Ảnh minh chứng cần chụp

Ảnh mail OTP test đã che, kết quả OTP và bảo mật credential.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.9.5-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://support.google.com/accounts/answer/185833>
