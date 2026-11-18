---
title: "Kiểm thử và trình diễn"
weight: 11
chapter: false
pre: "<b> 5.11. </b> "
---

# 5.11. Kiểm thử End-to-End và Live Demo

**Đây là kế hoạch test có thể lặp lại, không phải xác nhận tất cả đã pass.** Dùng tài khoản/đơn thử, API GET an toàn và ảnh đã che dữ liệu. Thay TODO bằng kết quả, timestamp, môi trường, minh chứng thật.

| ID | Ca kiểm thử | Mong đợi | Minh chứng thực tế |
|---|---|---|---|
| T01 | Mở frontend HTTPS | React tải qua CloudFront | TODO |
| T02 | Refresh route con React | SPA routing đúng | TODO |
| T03 | API HTTPS | ALB phản hồi, ECS target healthy | TODO |
| T04 | Guest xem catalog/giá | Đúng policy public | TODO |
| T05 | Admin duyệt + Gmail OTP | Customer hợp lệ mới login được | TODO |
| T06 | Customer thử gọi API duyệt Quote của Staff | Backend từ chối | TODO |
| T07 | Volume Pricing và duyệt Quote | Backend tính giá/kiểm quyền đúng | TODO |
| T08 | Đặt Order khi thiếu SKU | Không Order, không giữ tồn một phần | TODO |
| T09 | Webhook SePay thử hợp lệ | Xử lý đúng 1 lần | TODO |
| T10 | Webhook SePay sai/trùng | Không đổi paid sai hoặc double process | TODO |
| T11 | Delivery Staff hoàn tất chuyến | Đúng điều kiện nghiệp vụ | TODO |
| T12 | Endpoint AI BE → Bedrock | Đúng schema/permission sau test, hiện pending | TODO |
| T13 | WAF FE/BE | Đúng association; rule BE **Count** | TODO |
| T14 | CloudWatch Logs/Alarms → SNS | Log và mail alarm nếu thực sự có | TODO |
| T15 | CloudWatch RUM/Cognito | Có event từ FE thật, hiện pending | TODO |
| T16 | GitHub Actions FE/BE | SHA/digest/build khớp dịch vụ deploy | TODO |
| T17 | Cloudinary/Vietmap | Ảnh và bản đồ/địa chỉ dùng được | TODO |

## Lệnh test an toàn (điền hostname thật)

```powershell
curl.exe -I https://<FRONTEND_DOMAIN>/
curl.exe -i https://<API_DOMAIN>/<ACTUAL_PUBLIC_API_PATH>
Resolve-DnsName <FRONTEND_DOMAIN>
Resolve-DnsName <API_DOMAIN>
```

Không stress test phá hoại, không dùng chuyển khoản thật/địa chỉ thật. Không mặc định `/actuator/health` public; phải xem Swagger/OpenAPI.

## Live demo

- Frontend URL: `[TODO]`
- API domain (không kèm credential): `[TODO]`
- Link GitHub Actions FE/BE: `[TODO]`
- Ngày test và commit/image digest: `[TODO]`
- Ảnh/video minh chứng: `[TODO]`
- Chức năng còn pending: `Bedrock production API, RUM ingestion; WAF BE Count` (chỉ sửa khi có test thật).
