---
title: "Amazon S3"
weight: 2
chapter: false
pre: "<b> 5.5.2. </b> "
---

# 5.5.2. Amazon S3

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã dùng lưu frontend production.

## Mục tiêu và vai trò trong hệ thống

Lưu file frontend build; ảnh sản phẩm/avatar dùng Cloudinary, không phải S3 frontend.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Vào S3 → Buckets, chọn bucket đang chứa frontend build React (`dist/` hoặc `build/`).
2. Kiểm tra object `index.html`, JS/CSS, Cache-Control, Region, Block Public Access và bucket policy.
3. Đối chiếu CloudFront origin; nếu bucket private, xác nhận Origin Access Control (OAC) và policy cho CloudFront.
4. Kiểm tra GitHub Actions sync đúng thư mục build và không vô tình xóa object khác.
5. Khi lên bản SPA mới, chạy CloudFront invalidation phù hợp rồi tải lại web để xác nhận asset hash mới.
6. Không dùng bucket frontend để thay thế Cloudinary của ảnh sản phẩm/avatar.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** CloudFront tải asset thành công; nếu dùng OAC thì S3 không public; refresh route SPA đúng cấu hình.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Nếu đội triển khai kiểu S3 origin khác, mô tả cấu hình thực tế thay vì khẳng định có OAC.

## Ảnh minh chứng cần chụp

Objects/permission của bucket, origin CloudFront và web tải thành công.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.5.2-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Lệnh kiểm tra tham khảo (read-only)

```powershell
# Local sanity check of build folder (choose dist or build as your project uses)
Get-ChildItem .\dist -ErrorAction SilentlyContinue
```

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html>
