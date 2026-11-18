---
title: "SePay QR chuyển khoản và webhook"
weight: 4
chapter: false
pre: "<b> 5.9.4. </b> "
---

# 5.9.4. SePay QR chuyển khoản và webhook

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã được liệt kê tích hợp; cần xác minh webhook và chuyển trạng thái thanh toán.

## Mục tiêu và vai trò trong hệ thống

Tạo QR/chuyển khoản và webhook trạng thái giao dịch.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Kiểm tra config tích hợp SePay trong backend, endpoint, tài khoản merchant và URL callback; che token và thông tin ngân hàng.
2. Dùng **sandbox hoặc giao dịch nhỏ được nhóm cho phép** để lấy QR, xác nhận số tiền/mã đơn lấy từ backend, không tin FE tự báo đã trả tiền.
3. Kiểm tra webhook route production, dùng cơ chế xác thực/chữ ký/shared secret theo tài liệu SePay chính thức đang áp dụng.
4. Test callback hợp lệ trong môi trường phù hợp, kiểm tra order reference, tiền, loại tiền, idempotency và chống replay.
5. Gửi callback lỗi/trùng trong môi trường test để xác nhận không tự chuyển Order chưa trả thành paid hoặc trừ kho/giao trùng.
6. Đọc log webhook đã che dữ liệu và ghi trạng thái thanh toán thật; QR không phải bằng chứng đã thanh toán.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Sự kiện payment hợp lệ được xử lý một lần; callback giả/trùng không tự tạo trạng thái paid.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Phải đối chiếu cơ chế bảo mật webhook theo contract SePay thực tế; không tự đoán header chữ ký.

## Ảnh minh chứng cần chụp

QR test/mã tham chiếu đã che, cấu hình webhook, log callback hợp lệ/lỗi.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.9.4-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.sepay.vn/>
