---
title: "Amazon CloudFront"
weight: 2
chapter: false
pre: "<b> 5.7.2. </b> "
---

# 5.7.2. Amazon CloudFront

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Distribution frontend đã hoạt động.

## Mục tiêu và vai trò trong hệ thống

Phân phối React SPA từ S3 qua HTTPS/cache và liên kết WAF.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở CloudFront → Distributions; chọn distribution FE, ghi ID, alternate domain, trạng thái và behavior.
2. Xác nhận S3 origin đúng bucket và kiểm tra OAC/bucket policy nếu áp dụng.
3. Kiểm tra viewer certificate, redirect HTTPS, cache policy và cách trả asset tĩnh.
4. Kiểm tra fallback cho React SPA deep link bằng custom error/function/rewrite phù hợp; không chuyển mọi 403 thành index.html bừa bãi.
5. Kiểm tra Web ACL frontend đang gắn với CloudFront, tách riêng WAF backend ALB.
6. Mở domain thật, xem asset tải được và đối chiếu invalidation sau GitHub Actions deploy.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Domain FE trả trang/asset qua HTTPS và refresh route con hoạt động.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

CloudFront global, không vẽ trong một private/public subnet của VPC.

## Ảnh minh chứng cần chụp

Distribution, origin, TLS và network request của trình duyệt.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.7.2-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html>
