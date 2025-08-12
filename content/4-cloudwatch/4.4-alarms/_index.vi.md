---
title : "Thiết Lập cảnh báo CloudWatch Alarms"
date :  "2025-08-11" 
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

#### CloudWatch Alarms
ℹ️ **Information**: Amazon CloudWatch Alarms giúp giám sát metrics hoặc log-derived metrics và tự động kích hoạt hành động khi vượt ngưỡng.

1. Trở lại màn hình chính của CloudWatch.
    + Chọn **Alarms** ở menu bên trái.
    + Chọn **All alarms.**
    + Ấn chọn **Create alarm.**

![Alarm](/images/4.cloudwatch/alarm-001.png)

2. Chọn **Select metric.**

![Alarm](/images/4.cloudwatch/alarm-002.png)

Cửa sổ metrics hiện lên, trong **Custom namespaces**, chọn **k6-logs.**

![Alarm](/images/4.cloudwatch/alarm-003.png)

Chọn tiếp **Metrics with no dimensions**, chọn **/var/log/messages** và ấn chọn **Select metric.**

![Alarm](/images/4.cloudwatch/alarm-004.png)

3. Trong phần **Specify metric and conditions**, chọn **Period** là **1 minutes.**

![Alarm](/images/4.cloudwatch/alarm-005.png)

4. Trong phần **Conditions**
    + Threshold type: **Static.**
    + Điều kiện: **Greater** than **100**.
  
![Alarm](/images/4.cloudwatch/alarm-006.png)

💡 **Pro Tip**: Đường nét đứt ngang trên biểu đồ chỉ ra ngưỡng mà **Alarm** sẽ được kích hoạt. Khi số lượng lỗi vượt quá ngưỡng này, đó là dấu hiệu của sự cố tiềm ẩn trong ứng dụng cần được kiểm tra ngay lập tức.

Sau đó ấn **Next** để tiếp tục.
5. Giờ thì chúng ta cấu hình thông báo như sau
    + Alarm state trigger: **In alarm.**
    + Chọn **Create new topic.**
    + Tên topic là: `Error_logs_reach_10`.
    + Email thông báo tới: bạn sẽ nhập email của bạn vào, ở đây mình sẽ nhập của mình.
    + Ấn **Create topic.**
  
![Alarm](/images/4.cloudwatch/alarm-007.png)
![Alarm](/images/4.cloudwatch/alarm-008.png)

  + Ấn chọn **Next.**

![Alarm](/images/4.cloudwatch/alarm-008.png)

⚠️ **Warning**: Đảm bảo rằng địa chỉ email bạn cung cấp là chính xác và được kiểm tra thường xuyên. Nếu không xác nhận đăng ký SNS, bạn sẽ không nhận được thông báo khi alarm kích hoạt.

1. Ở bước cuối, nhập tên alarm là `PythonApplicationErrorAlarm` và ấn chọn **Next.**

![Alarm](/images/4.cloudwatch/alarm-009.png)

💡 **Pro Tip**: Đặt tên alarm có ý nghĩa và mô tả rõ mục đích giúp dễ dàng quản lý khi số lượng alarm tăng lên trong môi trường sản xuất thực tế.

  + Xem lại kết quả và ấn chọn **Create alarm.**
  
![Alarm](/images/4.cloudwatch/alarm-010.png)
![Alarm](/images/4.cloudwatch/alarm-011.png)

Kết quả

![Alarm](/images/4.cloudwatch/alarm-012.png)

  + Đăng nhập vào Gmail hoặc bất kì trang email nào mà bạn dùng. Bạn sẽ thấy một email được gửi tới từ **AWS Notification.**
  + Ấn chọn **Confirm subscription.**
    
![Alarm](/images/4.cloudwatch/alarm-013.png)
![Alarm](/images/4.cloudwatch/alarm-014.png)

🔒 **Security Note**: Việc xác nhận đăng ký SNS không chỉ kích hoạt thông báo mà còn là một biện pháp bảo mật, đảm bảo rằng chỉ những người dùng được ủy quyền mới nhận được thông báo về trạng thái hệ thống.

ℹ️ **Information**: Với CloudWatch Alarms đã thiết lập, bạn có thể mở rộng hệ thống giám sát bằng cách tích hợp với các dịch vụ khác như AWS Lambda để tự động khắc phục sự cố, hoặc AWS Systems Manager để thực hiện các hành động tự động trên tài nguyên bị ảnh hưởng.

