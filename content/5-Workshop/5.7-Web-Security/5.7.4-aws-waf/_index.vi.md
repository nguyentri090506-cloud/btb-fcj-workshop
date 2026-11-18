---
title: "AWS WAF (Frontend & Backend)"
weight: 4
chapter: false
pre: "<b> 5.7.4. </b> "
---

# 5.7.4. AWS WAF (Frontend & Backend)

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã có WAF; rule giới hạn ở BE hiện **Count**, không chặn.

## Mục tiêu và vai trò trong hệ thống

Web ACL xử lý request vào CloudFront và ALB (Count/Block theo từng rule).

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở AWS WAF → Web ACLs; xác định ACL global của CloudFront FE và ACL Regional gắn ALB BE (nếu có).
2. Kiểm tra resource association; WAF của CloudFront không tự bảo vệ API đang truy cập ALB trực tiếp.
3. Ghi tên rule, priority, điều kiện, managed rule và action đúng với production.
4. Với **rule giới hạn backend**, phải ghi action `Count`: chỉ đếm match và không tự block request.
5. Mở Traffic overview/sampled requests, lưu minh chứng CountedRequests bằng traffic hợp lệ; không tạo traffic tấn công để chụp hình.
6. Đánh giá false positive trước khi đề xuất chuyển sang Block và ghi quy trình phê duyệt.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Web ACL FE/BE đúng nơi và rule Count của BE được mô tả đúng, không tuyên bố đã chặn.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Action theo từng rule; Count-only chưa phải chặn request. WAF có thể phát sinh phí theo ACL/rule/request.

## Ảnh minh chứng cần chụp

Association CloudFront/ALB, action Count và thống kê request match.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.7.4-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/waf/latest/developerguide/web-acl-rule-actions.html>
