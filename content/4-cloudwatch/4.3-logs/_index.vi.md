---
title : "CloudWatch Logs"
date :  "2025-08-04" 
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

#### Tổng quan
ℹ️ **Information**: Amazon CloudWatch Logs cho phép bạn thu thập, lưu trữ và phân tích log từ ứng dụng, dịch vụ AWS hoặc công cụ kiểm thử như k6.Trong quy trình Performance Automation Testing, CloudWatch Logs giúp:
  + Lưu trữ kết quả test từ k6 để phân tích.
  + Tìm kiếm lỗi hoặc cảnh báo xuất hiện khi hệ thống chịu tải.
  + Tạo metric từ log để giám sát tự động trong CI/CD pipeline.

💡 **Pro Tip**: Việc phân tích logs hiệu quả không chỉ giúp khắc phục sự cố nhanh chóng mà còn hỗ trợ tối ưu hóa hiệu suất và phát hiện các mẫu hành vi bất thường trong hệ thống của bạn.

🔒 **Security Note**: CloudWatch Logs cũng đóng vai trò quan trọng trong việc tuân thủ các yêu cầu về bảo mật và kiểm toán, cho phép bạn lưu trữ logs an toàn và truy xuất chúng khi cần thiết.

#### CloudWatch Logs
  + Trong trang chính của CloudWatch.
    + Phần menu bên trái, mở rộng mục **Logs**
    + Chọn **Log groups**
    + Chọn **/aws/codebuild/fcjBookStorBuildProject**

![Logs](/Workshop-AWS/images/4.cloudwatch/logs-001.png)

💡 **Pro Tip**: Sử dụng thanh tìm kiếm giúp bạn nhanh chóng tìm thấy các log groups cụ thể trong môi trường có nhiều tài nguyên, tiết kiệm thời gian phân tích.

  + Chọn một instance bất kỳ để xem chi tiết logs

![Logs](/Workshop-AWS/images/4.cloudwatch/logs-002.png)

  + Trong giao diện logs, bạn có thể thấy các bản ghi từ instance này được tạo ra từ nhiều nguồn khác nhau như: dhclient, NET, ec2net, systemd…

![Logs](/Workshop-AWS/images/4.cloudwatch/logs-003.png)

ℹ️ **Information**: Các logs này cung cấp thông tin chi tiết về hoạt động của hệ thống, giúp bạn theo dõi các sự kiện, phát hiện lỗi và hiểu rõ hơn về cách hệ thống đang hoạt động.

#### CloudWatch Metric Filter
1. Quay lại màn hình chính của **CloudWatch**
    + Chọn **Log groups** từ menu bên trái
    + Chọn **/aws/codebuild/fcjBookStorBuildProject**

[Logs](/Workshop-AWS/images/4.cloudwatch/logs-001.png)

2. Trong giao diện của **/aws/codebuild/fcjBookStorBuildProject**
    + Mở rộng menu **Actions**
    + Chọn **Create metric filter**

![Logs](/Workshop-AWS/images/4.cloudwatch/logs-004.png)

3. Trong phần **Define Pattern**, cấu hình các thông tin sau:
    + Filter pattern: mở rộng dropdown và chọn **Warning**
    + Test pattern: mở rộng và chọn một instance (nên chọn instance mà chúng ta đã tạo processes ở các bước trước)

![Logs](/Workshop-AWS/images/4.cloudwatch/logs-005.png)

💡 **Pro Tip**: Việc kiểm thử pattern trước khi tạo metric filter giúp bạn xác nhận rằng filter sẽ bắt đúng các sự kiện mong muốn, tránh tình trạng thiếu dữ liệu hoặc dữ liệu không chính xác.

4. Trong phần **Create filter name** của **Assign metric**, nhập `PythonAppErrors`
  + Trong phần **Metric details**, cấu hình các thông tin sau:
    + Metric namespace: `k6-logs`
    + Metric name: `/var/log/messages - ERROR`
    + Metric value: **1**
    + Default value: **0**
    + Unit: mở rộng dropdown và chọn **Count**
    + Nhấn **Next**

![Logs](/Workshop-AWS/images/4.cloudwatch/logs-006.png)

⚠️ **Warning**: Việc đặt namespace và tên metric phù hợp rất quan trọng để dễ dàng tìm kiếm và phân loại metrics trong môi trường có nhiều ứng dụng. Hãy sử dụng quy ước đặt tên nhất quán trong toàn bộ hệ thống của bạn.

5. Xem lại cấu hình và nhấn **Create metric filter**
   
![Logs](/Workshop-AWS/images/4.cloudwatch/logs-007.png)
![Logs](/Workshop-AWS/images/4.cloudwatch/logs-008.png)

6. Trở lại **Metrics > All metrics**
    + Tìm kiếm với từ khóa `/var/log/messages` và `ERROR`
    + Chọn **k6-logs > Metrics with no dimensions**

![Logs](/Workshop-AWS/images/4.cloudwatch/logs-009.png)
![Logs](/Workshop-AWS/images/4.cloudwatch/logs-010.png)

ℹ️ **Information**: Bây giờ chúng ta đã có một metric được tạo từ các log WARNING. Metric này có thể được sử dụng để tạo biểu đồ, dashboards, và cảnh báo khi số lượng lỗi vượt quá ngưỡng cho phép.

💡 **Pro Tip**: Bạn có thể tạo nhiều metric filters khác nhau cho cùng một log group để theo dõi các loại sự kiện khác nhau, như ERROR, INFO, hoặc các mẫu tùy chỉnh phù hợp với ứng dụng của bạn.

🔒 **Security Note**: Metric filters là công cụ quan trọng để phát hiện các vấn đề bảo mật tiềm ẩn trong hệ thống của bạn. Hãy cân nhắc tạo các filters đặc biệt cho các sự kiện liên quan đến bảo mật như đăng nhập thất bại, thay đổi quyền, hoặc truy cập trái phép.

