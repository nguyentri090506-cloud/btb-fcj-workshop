---
title: "CloudWatch Metrics và Alarms"
weight: 2
chapter: false
pre: "<b> 5.8.2. </b> "
---

# 5.8.2. CloudWatch Metrics và Alarms

> **Hiện trạng theo nhóm BTB cung cấp (18/11/2026):** Đã cấu hình metric và alarm.

## Mục tiêu và vai trò trong hệ thống

Giám sát CPU/RAM ECS, lỗi/độ trễ/target ALB và kích hoạt cảnh báo.

## Thực hành: đối chiếu, ghi nhận và kiểm tra cấu hình production đang có

1. Mở CloudWatch → Metrics; chọn metric theo Cluster/Service ECS và ALB đang chạy thật.
2. Kiểm tra CPUUtilization/MemoryUtilization ECS, HTTPCode_Target_5XX_Count, TargetResponseTime, HealthyHostCount ALB nếu được bật.
3. Vào Alarms → All alarms, ghi tên, metric, period, statistic, số lần đánh giá và threshold từng alarm.
4. Kiểm tra action publish đúng SNS topic; ghi trạng thái `OK`, `ALARM`, hoặc `INSUFFICIENT_DATA` thực tế.
5. Nếu nhóm đã test alarm an toàn, đính kèm history/email có timestamp; chưa thử thì không tự đổi threshold production chỉ để chụp ảnh.
6. Đối chiếu alarm với ECS events/CloudWatch Logs để giải thích nguyên nhân chứ không chỉ chụp biểu đồ.

## Kết quả mong đợi và ghi nhận thực tế

**Mong đợi:** Alarm, SNS topic và đồ thị metric được đối chiếu với resource đang chạy.

**Thực tế:** `[BỔ SUNG SAU KHI TEST: kết quả, ngày/giờ, Region, resource, minh chứng]`

## Lưu ý vận hành và rủi ro

Không ghi “alarm thành công” nếu chưa thấy chuyển trạng thái và email thực tế.

## Ảnh minh chứng cần chụp

Đồ thị metric, cấu hình/trạng thái/history alarm, SNS topic.

**Đường dẫn gợi ý:** `static/images/5-workshop/5.8.2-01.png` (chụp Console thật; không tự tạo ảnh giả).

## Tài liệu tham khảo

<https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html>
