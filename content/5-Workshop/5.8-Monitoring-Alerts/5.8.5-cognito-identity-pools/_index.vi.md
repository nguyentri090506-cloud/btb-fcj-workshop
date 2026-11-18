---
title: "Amazon Cognito Identity Pools"
weight: 5
chapter: false
pre: "<b> 5.8.5. </b> "
---

# 5.8.5. Amazon Cognito Identity Pools

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã tạo Identity Pool cùng RUM.

## Mục tiêu và vai trò trong hệ thống

Cấp AWS credential tạm cho RUM client của trình duyệt theo cấu hình hiện tại.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở Cognito → Identity pools, tìm pool được RUM app monitor sử dụng (khác User Pool làm login BTB).
2. Kiểm tra cấu hình authenticated/unauthenticated identity thật và role IAM tương ứng.
3. Đối chiếu policy role unauth chỉ đủ cho RUM ingest (ví dụ `rum:PutRumEvents` trên monitor phù hợp), không cấp admin access.
4. Kiểm tra frontend đã deploy dùng đúng pool ID/Region, không nhúng access key dài hạn.
5. Quan sát request telemetry/lỗi AccessDenied trong DevTools và đối chiếu với dữ liệu RUM.
6. Ghi Cognito Identity Pools là **quyền cho RUM**, không đồng nhất với đăng nhập/OTP Customer qua Supabase/BTB.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Browser lấy credential tạm và gửi được event đến monitor (chưa test thì ghi pending).

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Identity Pools không chứng minh dự án dùng Cognito User Pools cho Customer auth.

## Ảnh minh chứng cần chụp

Pool ID/Region, policy role IAM giới hạn quyền và tích hợp RUM.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.8.5-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-RUM-get-started-authorization.html>
