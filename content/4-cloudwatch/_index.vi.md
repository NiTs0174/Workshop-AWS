---
title : "Tích Hợp Giám Sát Hiệu Suất với CloudWatch"
date :  "2025-08-11" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Tổng quan
ℹ️ **Information**: **Amazon CloudWatch** là dịch vụ giám sát và quan sát (observability) toàn diện của AWS, cho phép thu thập, theo dõi và phân tích metrics, logs, và sự kiện của hạ tầng và ứng dụng theo thời gian thực. Trong bối cảnh Performance Automation Testing in CI/CD, **CloudWatch** đóng vai trò là trung tâm giám sát hiệu năng — giúp tự động thu thập dữ liệu sau mỗi lần kiểm thử tải, phân tích kết quả, phát hiện bất thường và kích hoạt cảnh báo.


#### Lợi ích chính
💡 **Pro Tip**: Với **Amazon CloudWatch**, bạn có thể:
  + Giám sát toàn diện các tài nguyên AWS và ứng dụng của bạn
  + Thiết lập cảnh báo thông minh dựa trên ngưỡng tùy chỉnh
  + Tự động hóa phản hồi đối với các sự cố hoạt động
  + Tạo bảng điều khiển trực quan để theo dõi hiệu suất
  + Phân tích logs để khắc phục sự cố nhanh chóng

🔒 **Security Note**: Việc thiết lập giám sát đúng cách với **CloudWatch** không chỉ giúp tối ưu hiệu suất mà còn là một phần quan trọng trong chiến lược bảo mật, giúp phát hiện các hoạt động bất thường trong hệ thống của bạn.

#### Nội dung 
  - [CloudFormation](4.1-cloudformation/)
  - [CloudWatch Metric](4.2-metric/)
  - [CloudWatch Logs](4.3-logs/)
  - [CloudWatch Alarms](4.4-alarms/)
  - [CloudWatch Dashboards](4.5-dashboards/)