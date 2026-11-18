---
title: "Vietmap bản đồ và vị trí"
weight: 3
chapter: false
pre: "<b> 5.9.3. </b> "
---

# 5.9.3. Vietmap bản đồ và vị trí

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã liệt kê tích hợp; cần kiểm tra endpoint/key đang dùng production.

## Mục tiêu và vai trò trong hệ thống

Bản đồ, địa chỉ và khoảng cách giao hàng của BTB.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở màn Customer/Delivery Staff production có Vietmap, xác nhận tile/marker tải qua HTTPS.
2. Kiểm tra API key và origin/restriction theo cấu hình thật, che key trên screenshot.
3. Test điểm giao mẫu, xem tìm địa chỉ/geocoding và kết quả tuyến/quãng đường hiển thị.
4. Ghi nghiệp vụ demo BTB: một kho, Order có nhiều package/địa điểm, ETA minh họa theo 40 km/h chứ không cam kết thời gian đường thực.
5. Test xử lý timeout, quota, denied từ Vietmap và cách hiển thị fallback.
6. Chụp bản đồ dùng địa chỉ thử, không hiển thị địa chỉ thật của Customer.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Bản đồ, địa chỉ và khoảng cách hoạt động với dữ liệu thử theo giả định demo.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

ETA chỉ minh họa; không có GPS/đèn đỏ/kẹt xe thực và không đảm bảo đúng thời gian.

## Ảnh minh chứng cần chụp

Ảnh route và vị trí thử, che thông tin địa chỉ riêng.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.9.3-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://maps.vietmap.vn/>
