---
title : "Thu Thập & Phân Tích CloudWatch Metric"
date :  "2025-08-11" 
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

#### CloudWatch Metric
ℹ️ **Information**: Trong bối cảnh **Performance Automation Testing**, Metrics trong **Amazon CloudWatch** đóng vai trò như “bộ cảm biến” cho toàn bộ hệ thống. Chúng cung cấp dữ liệu định lượng về hiệu suất của ứng dụng, hạ tầng và quy trình kiểm thử.

💡 **Pro Tip**: **Metrics** là nền tảng để xây dựng hệ thống giám sát hiệu năng tự động, hỗ trợ thiết lập baseline, phát hiện regression, kích hoạt cảnh báo và đề xuất tối ưu hóa.

🔒 **Security Note**: Giám sát hiệu năng không chỉ phục vụ tối ưu hóa tốc độ và tài nguyên, mà còn giúp phát hiện sớm các hành vi bất thường có thể liên quan đến sự cố bảo mật hoặc tấn công DDoS.

#### Xem các Metrics
ℹ️ **Information**: Trong phần này, chúng ta sẽ thực hành cách xem và phân tích các metrics trong Amazon CloudWatch, giúp bạn hiểu rõ hơn về hiệu suất của các tài nguyên AWS.

1. Truy cập **AWS Management Console**
    + Tìm kiếm dịch vụ **CloudWatch** trong thanh tìm kiếm
    + Chọn **CloudWatch** từ kết quả tìm kiếm
  
![Metric](/Workshop-AWS/images/4.cloudwatch/metrics-001.png)

1. Trong giao diện **CloudWatch**
    + Mở rộng phần **Metrics** ở menu bên trái
    + Chọn **All metrics**
  
![Metric](/Workshop-AWS/images/4.cloudwatch/metrics-002.png)

  + Trong giao diện biểu đồ metrics, nhập `từ khóa` vào ô tìm kiếm
  + Từ kết quả tìm kiếm, chọn **kết quả mong muốn**

![Metric](/Workshop-AWS/images/4.cloudwatch/metrics-007.png)
![Metric](/Workshop-AWS/images/4.cloudwatch/metrics-003.png)

💡 **Pro Tip**: Khi sử dụng thanh tìm kiếm, CloudWatch mặc định sẽ tìm theo **Metric name**, giúp bạn nhanh chóng lọc ra các metrics cụ thể cần theo dõi.  

1. Tick chọn các nhiều metric để so sánh, quan sát biểu đồ và ghi nhận:
    + Thời điểm CPU tăng đột biến.
    + Thời điểm NetworkOut cao nhất (giai đoạn gửi nhiều request).
    + Thời gian xử lý request (metric từ k6).
  
![Metric](/Workshop-AWS/images/4.cloudwatch/metrics-004.png)

⚠️ **Warning**: Khi hiển thị nhiều metrics có đơn vị đo khác nhau trên cùng một biểu đồ, việc phân tích có thể trở nên khó khăn. Trong phần tiếp theo, chúng ta sẽ tìm hiểu cách tùy chỉnh biểu đồ để có cái nhìn trực quan hơn.

