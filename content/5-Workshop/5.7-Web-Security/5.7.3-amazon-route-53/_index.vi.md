---
title: "Amazon Route 53"
weight: 3
chapter: false
pre: "<b> 5.7.3. </b> "
---

# 5.7.3. Amazon Route 53

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** DNS đã cấu hình.

## Mục tiêu và vai trò trong hệ thống

Bản ghi DNS trỏ hostname frontend về CloudFront và API về ALB.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở Route 53 → Hosted zones, xác định public hosted zone của domain BTB.
2. Ghi alias/CNAME của tên miền FE và xác nhận trỏ đúng CloudFront distribution.
3. Ghi alias của API hostname và xác nhận trỏ đến ALB DNS name.
4. Kiểm tra TTL và bản ghi DNS validation cho ACM đang được duy trì.
5. Dùng `Resolve-DnsName` hoặc `nslookup` với cả hai domain thực tế rồi đối chiếu đích DNS.
6. Gọi HTTPS từng domain, ghi frontend/API hoạt động theo cấu hình.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** DNS FE/API resolve đúng và HTTPS trả đúng dịch vụ.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Tên miền/hosted zone phải do nhóm kiểm chứng; không lấy tên ví dụ ghi như production.

## Ảnh minh chứng cần chụp

Record DNS, đích resolve và ảnh HTTPS trình duyệt.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.7.3-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Lệnh kiểm tra tham khảo (read-only)

```powershell
# Windows PowerShell — replace with actual public names
Resolve-DnsName <FRONTEND_DOMAIN>
Resolve-DnsName <API_DOMAIN>
```

## Tài liệu tham khảo

<https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html>
