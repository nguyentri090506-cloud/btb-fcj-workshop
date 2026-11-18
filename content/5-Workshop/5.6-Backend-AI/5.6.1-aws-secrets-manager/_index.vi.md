---
title: "AWS Secrets Manager"
weight: 1
chapter: false
pre: "<b> 5.6.1. </b> "
---

# 5.6.1. AWS Secrets Manager

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã tạo secret cho BE; cần kiểm tra key và cách task nhận secret.

## Mục tiêu và vai trò trong hệ thống

Lưu cấu hình nhạy cảm của BE: database, AI, webhook, mail.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở Secrets Manager → Secrets và tìm secret backend theo tên; không cần xem giá trị bí mật.
2. Kiểm tra Region, tên/ARN, rotation (nếu có), thời điểm sửa và KMS.
3. Ở ECS task definition → Container → Secrets, đối chiếu secret key với biến môi trường; nếu app tự fetch runtime thì mô tả luồng đó.
4. Xác nhận execution role có quyền lấy secret trong task definition; nếu app gọi API Secrets Manager lúc chạy thì kiểm tra task role riêng.
5. Kiểm tra log BE không lộ secret hoặc connection string; ghi cách redeploy khi đổi credential.
6. Chỉ chụp tên secret và cấu hình tham chiếu, tuyệt đối không chụp màn hình `Retrieve secret value`.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** ECS lấy secret bằng role phù hợp, task mới khởi động được và không lộ credential.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Đổi secret đã inject qua env thường cần deploy/restart task; không mặc định tự cập nhật runtime.

## Ảnh minh chứng cần chụp

Metadata secret và đường dẫn tham chiếu từ ECS (che giá trị).

**Đường dẫn gợi ý:** `static/images/5-workshop/5.6.1-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonECS/latest/developerguide/specifying-sensitive-data-secrets.html>
