---
title : "Dọn Dẹp Tài Nguyên"
date :  "2025-08-11" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

{{% notice note %}}
  Sẽ mất một chút thời gian để hoàn thành việc dọn dẹp
{{% /notice %}}

1. Làm trống S3 bucket.
    + Mở **AWS S3 console**.
    + Chọn **fcj-book-shop-by-myself**.
    + Nhấp vào **Empty**.
    + Nhập `permanently delete`.
    + Nhấp vào **Empty**.
    + Làm tương tự cho các bucket bắt đầu bằng **aws-sam-cli-managed-default-**, **book-image-resize-shop-by-myself** và **codepipeline-us-east-1-**.

2. Xóa pipeline.
    + Mở **AWS CodePipeline console.**
    + Chọn pipeline **fcjBookStoreFEPipeline**.
    + Nhấp vào **Delete pipeline.**
    + Nhập `delete`.
    + Nhấp vào **Delete**.
    + Làm tương tự cho **fcjBookStorePipeline**.

3. Xóa dự án CodeBuild.
    + Mở **AWS CodeBuild console**.
    + Chọn dự án Build **fcjBookStoreBuildProject**.
    + Nhấp vào Actions, sau đó nhấp vào **Delete**.
    + Nhập `delete`.
    + Nhấp vào **Delete**.

4. Xóa kết nối giữa Gitlab và AWS.
    + Mở **AWS CodeBuild console**.
    + Nhấp vào **Settings** trên menu bên trái và nhấp vào **Connections** trong dropdown.
    + Chọn **fcjBookStoreGitlabConnection**.
    + Nhấp vào **Delete**.
    + Nhập `delete`.
    + Nhấp vào **Delete**.

5. Xóa các stack CloudFormation.
  + Trên thanh tìm kiếm dịch vụ AWS:
    + Nhập `CloudFormation`.
    + Chọn **CloudFormation.**
![Cloudformation](/Workshop-AWS/images/5.clean/clean-cloudformation-004.png)

  + Trong CloudFormation Console:
    + Chọn stack đã tạo trong workshop này.
    + Ấn chọn **Delete.**
![Cloudformation](/Workshop-AWS/images/5.clean/clean-cloudformation-001.png)

  + Trong hộp thoại xác nhận:
    + Ấn chọn **Delete** để xác nhận việc xóa stack.
![Cloudformation](/Workshop-AWS/images/5.clean/clean-cloudformation-002.png)

💡 **Pro Tip**: Quá trình xóa stack có thể mất vài phút tùy thuộc vào số lượng và độ phức tạp của tài nguyên. Bạn có thể theo dõi tiến trình trong tab “Events” của stack.

  + Chờ đợi quá trình xóa hoàn tất:
    + Stack sẽ hiển thị trạng thái “DELETE_IN_PROGRESS” trong quá trình xóa.
    + Sau khi hoàn tất, stack sẽ biến mất khỏi danh sách.
![Cloudformation](/Workshop-AWS/images/5.clean/clean-cloudformation-003.png)

6. Xóa bucket codepipeline-us-east-1-….
    + Mở AWS **S3 console**.
    + Chọn **codepipeline-us-east-1-…**.
    + Nhấp vào **Delete**.
    + Nhập `codepipeline-us-east-1-....`
    + Nhấp vào **Delete bucket.**

7. Xóa kho Git.
{{% notice note %}}
  Làm theo tài liệu này: [Xóa dự án Gitlab.](https://docs.gitlab.com/ee/user/project/working_with_projects.html#delete-a-project)
{{% /notice %}}

ℹ️ **Information**: Sau khi hoàn thành workshop, việc dọn dẹp tài nguyên là bước quan trọng để tránh phát sinh chi phí không cần thiết. 

⚠️ **Warning**: Mặc dù các tài nguyên EC2 và các dịch vụ liên quan sẽ bị xóa ngay lập tức, CloudWatch Metrics và Logs sẽ vẫn tồn tại trong hệ thống AWS của bạn tối đa 15 tháng theo chính sách lưu trữ mặc định.

🔒 **Security Note**: Việc dọn dẹp tài nguyên không chỉ giúp tiết kiệm chi phí mà còn là biện pháp bảo mật tốt, giảm thiểu bề mặt tấn công tiềm ẩn trong môi trường AWS của bạn.

