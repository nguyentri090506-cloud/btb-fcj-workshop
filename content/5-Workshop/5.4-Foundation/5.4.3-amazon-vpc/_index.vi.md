---
title: "Amazon VPC"
weight: 3
chapter: false
pre: "<b> 5.4.3. </b> "
---

# 5.4.3. Amazon VPC

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã có VPC, route, IGW; cần kiểm tra vị trí subnet và đường outbound thực tế.

## Mục tiêu và vai trò trong hệ thống

Mạng cho ALB public và ECS backend; subnet, route table, Internet Gateway.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Vào VPC → Your VPCs, chọn VPC BTB hiện có; ghi Region, VPC ID, CIDR thực tế, không chép CIDR ví dụ trên sơ đồ.
2. Mở Resource map và Subnets; ghi AZ, subnet public/private và route-table association đã cấu hình.
3. Kiểm tra Internet Gateway và public route; ALB public cần route/ingress phù hợp để nhận traffic internet.
4. Xác nhận vị trí ECS task và đường outbound tới Supabase, Cloudinary, Vietmap, SePay, Bedrock và SMTP; Internet Gateway không tự cấp internet cho ECS private.
5. Kiểm tra security group của ALB cho HTTPS hợp lệ và security group ECS chỉ cho phép cổng BE từ ALB SG.
6. Chụp VPC map, route tables, SG và thông số network của ECS; nếu chưa xác nhận đường private route thì ghi chưa xác minh.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** ALB health check đúng, ECS truy cập được dịch vụ cần dùng và cổng BE không mở trực tiếp ra Internet.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Subnet và số AZ phải lấy từ Console. Không mặc định hệ thống đã có NAT Gateway hay VPC endpoint.

## Ảnh minh chứng cần chụp

VPC resource map, route subnet, SG inbound/outbound, ECS task networking.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.4.3-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html>
