---
title: "Supabase PostgreSQL và xác thực"
weight: 1
chapter: false
pre: "<b> 5.9.1. </b> "
---

# 5.9.1. Supabase PostgreSQL và xác thực

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Trong danh sách production; cần xác nhận phân chia Supabase Auth/JWT với Spring Boot thực tế.

## Mục tiêu và vai trò trong hệ thống

Database PostgreSQL và thành phần xác thực được nhóm báo cáo đang dùng.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Vào dashboard Supabase, ghi Region và network policy; không sao chép mật khẩu DB hoặc service-role key.
2. Xác minh kết nối PostgreSQL của Spring Boot và phần nào dùng Supabase Auth; đối chiếu Spring Security/JWT production để giải quyết mâu thuẫn tài liệu cũ.
3. Kiểm tra ECS truy cập Supabase qua TLS bằng đường outbound và DNS/port thực tế.
4. Test API Spring Boot dạng GET bằng dữ liệu test; xem log nếu lỗi DNS, TLS, pool hoặc timeout.
5. Kiểm thử login/onboarding bằng tài khoản test theo cơ chế xác thực đang chạy, phân biệt OTP với JWT.
6. Không nhầm anon/public key với service-role key; ràng buộc ownership/role nghiệp vụ tại backend.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Có minh chứng kết nối DB và xác thực; kiến trúc ghi đúng bên phát hành/kiểm tra token.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Master context ghi Supabase Auth không thống nhất; danh sách production mới hơn nhưng vẫn cần đối chiếu code/cấu hình.

## Ảnh minh chứng cần chụp

Cấu hình Supabase (che bí mật), test kết nối backend, response auth test.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.9.1-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://supabase.com/docs/guides/database/overview>
