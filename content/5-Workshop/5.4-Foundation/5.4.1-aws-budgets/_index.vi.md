---
title: "AWS Budgets"
weight: 1
chapter: false
pre: "<b> 5.4.1. </b> "
---

# 5.4.1. AWS Budgets

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã tạo budget; cần đối chiếu số tiền, ngưỡng và email nhận.

## Mục tiêu và vai trò trong hệ thống

Giám sát chi phí và cảnh báo ngân sách của hạ tầng BTB production.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Vào Billing and Cost Management → Budgets → kiểm tra budget BTB đã tồn tại trước khi chỉnh sửa.
2. Ghi loại budget (cost), chu kỳ (monthly), tiền tệ, phạm vi và ngưỡng cảnh báo actual/forecast.
3. Kiểm tra email nhận thông báo, trạng thái xác nhận và khả năng nhận thư của nhóm.
4. So sánh chi phí thực tế/dự báo với ECS, ALB, CloudFront, WAF và logging.
5. Nếu lab chưa có budget riêng, tạo cost budget với ngưỡng *ví dụ* được nhóm chốt; không bịa ngân sách production.
6. Chụp thông tin cần thiết; không khẳng định hệ thống đã gửi cảnh báo nếu chưa có email thực tế.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Có budget; ngưỡng và nơi nhận đúng dữ liệu ghi lại; chỉ đánh dấu email thành công khi có minh chứng.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Budgets không tự khóa chi tiêu; tài nguyên production vẫn có thể tính phí.

## Ảnh minh chứng cần chụp

Cấu hình budget, người nhận email và đồ thị chi phí.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.4.1-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html>
