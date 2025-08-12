---
title : "Giới Thiệu"
date :  "2025-08-11" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
### Tổng Quan
Workshop này hướng dẫn cách xây dựng hệ thống kiểm thử hiệu năng tự động tích hợp vào quy trình CI/CD, sử dụng các dịch vụ AWS và công cụ mã nguồn mở. Bạn sẽ học cách thực hiện kiểm thử tải bằng công cụ k6, tự động phân tích kết quả, tích hợp giám sát hiệu năng với AWS CloudWatch, thiết lập hệ thống cảnh báo khi có bất thường và tạo báo cáo hiệu năng tự động. 

#### CI/CD
  + **CI - Continuous Integration** là một phương pháp phát triển phần mềm mà trong đó các nhà phát triển thường xuyên commit và push các thay đổi lên các shared repository. Bằng cách nạp và hợp nhất các thay đổi từ nhiều nhà phát triển khác nhau, vì vậy giảm thiểu nguy cơ xung đột. Trước mỗi lần commit, các nhà phát triển có thể chạy các unit test trên mã nguồn như một kiểm tra bổ sung trước khi tích hợp. Một continuous integration tự động build và chạy các bài kiểm tra trên các mã nguồn thay đổi để phát hiện bất kỳ lỗi nào ngay lập tức.

  + **CD - Continuous Delivery** là một phương pháp phát triển phần mềm mở rộng Continuous Integration trong đó mã nguồn được tự động chuẩn bị để triển khai cho một production instance. Sau khi build, build artifact với các thay đổi mới được triển khai cho một staging instance nơi chạy các bài kiểm tra nâng cao (integration, acceptance, load, end-to-end, etc.). Nếu cần, build artifact tự động được triển khai tới production instance sau khi được duyệt thủ công

  + **Continuous Delivery** là một phương pháp phát triển phần mềm mở rộng Continuous Delivery trong đó các thay đổi mã nguồn được triển khai tự động đến một production instance. Sự khác biệt giữa Continuous Delivery và Continuous Deployment ở bước kiểm duyệt thủ công. Với Continuous Delivery, việc triển khai diễn ra tự động sau khi kiểm duyệt thủ công. Với Continuous Delivery, việc triển khai diễn ra tự động mà không cần phê duyệt thủ công.

#### Performance Testing
**Performance Testing** là kỹ thuật kiểm thử nhằm xác định băng thông, khả năng xử lý, khả năng mở rộng hay nói chung là hiệu năng của hệ thống dưới khối lượng truy cập, khối được công việc xác định. Kết quả của kiểm thử hiệu năng phục vụ việc điều tra, đo lường, đánh giá hiệu năng thực của hệ thống.

#### k6
  + **k6** tên đầy đủ là Grafana k6, là một công cụ hỗ trợ load testing được phát triển bởi Grafana Labs và cộng đồng, nó là dự án mã nguồn mở và có thể mở rộng. k6 hỗ trợ tốt cho mô hình CI/CD, dễ dàng tích hợp vào các CI/CD tools như Jenkins, Azure Pipelines.

  + **k6** được phát triển bằng Go tuy nhiên test script được viết bằng JavaScript ES6, điều này giúp chúng ta dễ dàng tiếp cận và sử dụng. k6 cũng phát triển dịch vụ k6 Cloud mạnh mẽ, với nhiều tính năng đặc biệt như tạo test script với giao diện thân thiện, chạy test với số lượng lớn cùng nhiều tính năng khác.

### Kiến Trúc Workshop

![Architecture](/Workshop-AWS/images/arc-cicd-be.png)

- **k6** cho kiểm thử tải, xác thực hiệu năng và gửi metrics đến CloudWatch.
- **AWS CodePipeline** Tự động hóa pipeline CI/CD.
- **AWS CodeBuild** Chạy job kiểm thử k6 trong pipeline.
- **Amazon S3** Lưu trữ test script và báo cáo kết quả kiểm thử
- **CloudWatch** 
  - **Metrics** – Thu thập metrics về hiệu năng từ k6 và ứng dụng.
  - **Logs** – Lưu log kết quả test và log hệ thống.
  - **Alarms** – Gửi cảnh báo khi hiệu năng vượt ngưỡng.
  - **Logs Insights** – Phân tích sâu log kiểm thử để tìm vấn đề.
  - **Dashboard** – Tổng hợp metrics & logs trên một giao diện trực quan.

Qua workshop này, bạn sẽ:
- Xây dựng quy trình CI/CD với kiểm thử hiệu năng tích hợp
- Sử dụng k6 kiểm tra khả năng chịu tải và độ ổn định của hệ thống.
- Phân tích kết quả kiểm thử tự động thông qua CloudWatch Metrics, Logs và Logs Insights.
- Tích hợp giám sát hiệu năng với AWS CloudWatch, bao gồm thu thập metrics, logs, và hiển thị trên dashboard.
- Quản lý đường cơ sở (baseline) hiệu năng, so sánh kết quả các lần kiểm thử để phát hiện hiệu năng suy giảm (performance regression).
- Thiết lập hệ thống cảnh báo bằng CloudWatch Alarms để nhận thông báo khi hiệu năng vượt ngưỡng.
- Tự động hóa báo cáo hiệu năng, tổng hợp thông tin từ logs và metrics.

