---
title: "Amazon Bedrock"
weight: 4
chapter: false
pre: "<b> 5.6.4. </b> "
---

# 5.6.4. Amazon Bedrock

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã cấu hình model và IAM; endpoint AI trên backend production chưa xác minh.

## Mục tiêu và vai trò trong hệ thống

Cung cấp AI model inference cho backend/Generate UI; quyền nghiệp vụ vẫn do Spring Boot kiểm soát.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở Amazon Bedrock đúng Region, ghi model ID/inference profile ứng dụng sử dụng và quyền model tại Region đó.
2. Kiểm tra IAM policy của ECS task role cho thao tác invoke model và ARN/resource cần dùng.
3. Đối chiếu cấu hình provider trong Secrets Manager/ECS runtime mà không in API key, prompt có thông tin cá nhân hoặc credential.
4. Gửi request kiểm thử **không nhạy cảm** đến endpoint AI thật của BE; nếu chưa biết đường dẫn thì xem Swagger/OpenAPI thay vì bịa URL.
5. Đọc log AI/Bedrock và độ trễ; phân biệt lỗi quyền model, timeout, throttling và validation ở ứng dụng.
6. Ghi rõ đã cấu hình hay đã kiểm thử production; AI không tự duyệt Quote, đổi giá, giữ tồn hoặc xác thực quyền.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Request test gọi được endpoint AI và trả dữ liệu hợp lệ sau phân quyền; chưa chạy thì ghi pending.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Tài liệu kế hoạch cũ nói Gemini; cập nhật nhóm mới nói Bedrock. Cần xác minh provider trong backend rồi mới khẳng định đã chuyển hoàn toàn.

## Ảnh minh chứng cần chụp

Model/profile, phạm vi IAM, kết quả test đã che dữ liệu và log.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.6.4-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html>
