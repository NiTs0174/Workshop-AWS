---
title : "CloudWatch Dashboards"
date :  "2025-08-11" 
weight : 5
chapter : false
pre : " <b> 4.5 </b> "
---

ℹ️ **Information**: Amazon CloudWatch Dashboards cho phép tạo bảng điều khiển tùy chỉnh để giám sát metrics, logs, và alarms trong thời gian thực.
Trong Performance Automation Testing, dashboard giúp: Theo dõi kết quả test (latency, error rate, throughput) trực quan; xem trạng thái alarm (ví dụ: vượt ngưỡng lỗi hoặc độ trễ); giúp team phát hiện sự cố nhanh hơn so với chỉ xem log hoặc email thông báo.

#### CloudWatch Dashboards
1. Thêm alarm đã tạo vào Dashboard:
    + Chọn **k6TestingAlarm**
    + Mở rộng menu **Actions**
    + Chọn **Add to dashboard**
  
![Board](/Workshop-AWS/images/4.cloudwatch/board-001.png)

  + Trong hộp thoại **Add to dashboard**, chọn **Create new**
  
![Board](/Workshop-AWS/images/4.cloudwatch/board-002.png)

  + Cấu hình Dashboard mới:
    + Nhập tên dashboard: `CloudWatch-Workshop`
    + Nhấn **Create**
    + Nhấn **Add to dashboard**

![Board](/Workshop-AWS/images/4.cloudwatch/board-003.png)

💡 **Pro Tip**: Đặt tên dashboard có ý nghĩa và phân loại rõ ràng sẽ giúp bạn dễ dàng quản lý khi số lượng dashboards tăng lên trong môi trường thực tế. Cân nhắc sử dụng các tiền tố như “Prod-”, “Dev-”, hoặc tên ứng dụng để phân loại.

Dưới đây là dashboard vừa được tạo:

![Board](/Workshop-AWS/images/4.cloudwatch/board-004.png)

ℹ️ **Information**: CloudWatch Dashboards hỗ trợ nhiều loại widget khác nhau như biểu đồ, số liệu đơn, bảng, văn bản và nhiều hơn nữa. Mỗi widget có thể được tùy chỉnh về kích thước, vị trí và hiển thị dữ liệu.

Bạn có thể thực hiện nhiều thao tác tùy chỉnh trên widget này:

![Board](/Workshop-AWS/images/4.cloudwatch/board-005.png)
![Board](/Workshop-AWS/images/4.cloudwatch/board-006.png)

🔒 **Security Note**: Dashboards có thể được chia sẻ với người dùng khác trong tổ chức của bạn hoặc thậm chí công khai (không yêu cầu đăng nhập AWS). Hãy cẩn thận khi chia sẻ dashboards có chứa thông tin nhạy cảm về cơ sở hạ tầng của bạn.

⚠️ **Warning**: CloudWatch Dashboards có giới hạn 500 widgets trên mỗi dashboard và 20.000 metrics trên tất cả các dashboards. Trong môi trường sản xuất lớn, hãy cân nhắc tạo nhiều dashboards chuyên biệt thay vì một dashboard quá lớn và phức tạp.

