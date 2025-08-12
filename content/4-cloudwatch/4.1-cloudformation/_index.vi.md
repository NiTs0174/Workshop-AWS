---
title : "Triển khai CloudFormation Stack"
date :  "2025-08-11" 
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

### Tổng quan
ℹ️ **Information**: Trong phần này, chúng ta sẽ thiết lập môi trường lab bằng cách triển khai một **AWS CloudFormation Stack**. Việc sử dụng CloudFormation giúp triển khai nhanh chóng và đồng bộ tất cả các tài nguyên AWS cần thiết cho workshop.

ℹ️ **Information**: Thông qua việc triển khai Stack, chúng ta đảm bảo mọi thành phần phục vụ **Performance Automation Testing** được cấu hình sẵn sàng, thống nhất và dễ dàng tái sử dụng. Điều này giúp giảm thiểu thời gian cài đặt thủ công, tránh sai sót cấu hình, đồng thời tối ưu hóa quy trình thử nghiệm hiệu năng trong pipeline CI/CD.

### Triển khai CloudFormation Stack
1. Truy cập vào **AWS Management Console**
    + Tìm kiếm dịch vụ **CloudFormation** trong thanh tìm kiếm
    + Chọn **CloudFormation** từ kết quả tìm kiếm
  
![CloudFormation](/images/4.cloudwatch/cloudformation-001.png)

2. Trong giao diện **CloudFormation**
    + Chọn **Create stack**
    + Chọn **With new resources (standard)**
  
![CloudFormation](/images/4.cloudwatch/cloudformation-002.png)

3. Trong giao diện **Create stack**   
    + Trong phần **Prerequisite - Prepare template**, chọn **Choose an existing template**
    + Tiếp theo chọn **Sync from Git**
    + Ấn **Next**

![CloudFormation](/images/4.cloudwatch/cloudformation-003.png)

4. Cấu hình thông tin Stack
    + Stack name: Nhập `FCJ-CloudWatch-Workshop` (hoặc một tên dễ nhớ khác).
    + Chọn **Link a Git repository**.
    + Chọn **GitLab**.
    + Ở phần **Connection** chọn `fcjBookStoreGitLabConnection` (Đã liên kết ở **Codepipeline** )
    ![CloudFormation](/images/4.cloudwatch/cloudformation-004.png)

    + Role Name: Nhập `FCJ-CloudWatch-Workshop`.
    + Ở phần Template file path điền `template.yml`.
    + Ấn **Next**
    ![CloudFormation](/images/4.cloudwatch/cloudformation-005.png)

5. Cấu hình tùy chọn Stack  
  ⚠️ **Warning**: Đảm bảo bạn đã tích vào ô xác nhận IAM resources để CloudFormation có thể tạo các tài nguyên IAM cần thiết.
    + Không cần thay đổi cấu hình mặc định trên trang này
    + Cuộn xuống dưới cùng
    + Tích chọn **I acknowledge that CloudFormation might create IAM resources with custom namesAWS**
    + Ấn **Next**

![CloudFormation](/images/4.cloudwatch/cloudformation-006.png)

6. Xem lại và tạo Stack
    + Kiểm tra lại tất cả thông tin cấu hình
    + Cuộn xuống dưới cùng và ấn **Submit** để bắt đầu tạo Stack

![CloudFormation](/images/4.cloudwatch/cloudformation-007.png)

7. Theo dõi quá trình triển khai
  ℹ️ **Information**: Quá trình triển khai Stack có thể mất khoảng 5 phút để hoàn tất. Trong thời gian này, CloudFormation sẽ tự động tạo tất cả tài nguyên cần thiết cho workshop.

![CloudFormation](/images/4.cloudwatch/cloudformation-008.png)

### Xác nhận triển khai thành công
🔒 **Security Note**: Sau khi triển khai thành công, hãy kiểm tra tab **Outputs** của Stack để lấy thông tin về các tài nguyên đã được tạo, bao gồm các URL và thông tin truy cập cần thiết cho các bước tiếp theo.

![CloudFormation](/images/4.cloudwatch/cloudformation-009.png)

💡 **Pro Tip**: Khi Stack hiển thị trạng thái **CREATE_COMPLETE** với màu xanh lá, điều này xác nhận rằng tất cả tài nguyên đã được triển khai thành công và bạn đã sẵn sàng để tiếp tục với các bài thực hành **Amazon CloudWatch**.

