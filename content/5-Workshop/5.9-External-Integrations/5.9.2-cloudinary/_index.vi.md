---
title: "Cloudinary lưu trữ ảnh"
weight: 2
chapter: false
pre: "<b> 5.9.2. </b> "
---

# 5.9.2. Cloudinary lưu trữ ảnh

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã dùng để lưu ảnh/media, bao gồm avatar.

## Mục tiêu và vai trò trong hệ thống

Lưu ảnh sản phẩm, nội dung và avatar BTB; độc lập với S3 frontend.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở Cloudinary dashboard/folder, ghi cấu trúc ảnh; chỉ lưu URL/public_id được phép, không lộ API secret.
2. Trên web React production, kiểm tra ảnh card sản phẩm/brand/avatar tải đúng từ Cloudinary CDN.
3. Nếu test upload, dùng tài khoản/ảnh thử và luồng upload được backend ký hoặc proxy, không bật upload unsigned tự do.
4. Kiểm tra định dạng, dung lượng ảnh và quyền sở hữu khi ảnh là dữ liệu Customer.
5. Xác minh fallback ảnh hỏng và cách lưu public_id/secure_url nhất quán trong backend.
6. Giải thích S3 là frontend static build, Cloudinary là ảnh/media trong sơ đồ.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Ảnh hiển thị đúng; upload test có kiểm quyền; API secret không bị lộ.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Tên folder/public_id cần lấy thật; không tự đặt làm như production.

## Ảnh minh chứng cần chụp

URL ảnh trên web, metadata asset và xác nhận upload đã che dữ liệu.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.9.2-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://cloudinary.com/documentation/image_upload_api_reference>
