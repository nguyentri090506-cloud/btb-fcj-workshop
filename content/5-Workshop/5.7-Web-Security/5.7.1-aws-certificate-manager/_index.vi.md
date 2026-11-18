---
title: "AWS Certificate Manager (ACM)"
weight: 1
chapter: false
pre: "<b> 5.7.1. </b> "
---

# 5.7.1. AWS Certificate Manager (ACM)

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã cấp và sử dụng.

## Mục tiêu và vai trò trong hệ thống

Cấp TLS cho tên miền frontend CloudFront và backend ALB.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Vào ACM; kiểm tra chứng chỉ frontend ở **us-east-1** dành cho custom domain CloudFront, ghi tên miền được cover.
2. Chuyển sang Region của ALB và kiểm tra chứng chỉ cho API hostname.
3. Xác nhận trạng thái `Issued`, đúng hostname và có cách xác minh/renew phù hợp.
4. Đối chiếu Viewer certificate trên CloudFront và HTTPS listener của ALB để chắc chắn đã attach đúng chứng chỉ.
5. Test FE và API qua HTTPS bằng browser/curl, không còn lỗi hostname hoặc certificate.
6. Ghi tình trạng hết hạn/gia hạn, không lưu khóa riêng hay thông tin nhạy cảm.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Hai đường HTTPS dùng chứng chỉ đúng hostname, trình duyệt không cảnh báo.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

CloudFront dùng ACM tại us-east-1; ALB cần chứng chỉ tại Region của ALB.

## Ảnh minh chứng cần chụp

Metadata chứng chỉ, nơi gắn CloudFront/ALB và HTTPS thực tế.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.7.1-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cnames-and-https-requirements.html>
