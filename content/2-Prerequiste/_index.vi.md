---
title : "Chuẩn bị"
date :  "2025-08-11" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

### Triển khai trên Local
Trước khi chúng ta đi vào nội dung chính của workshop này, chúng ta cần phải cài đặt ứng dụng web. Tải xuống mã nguồn dưới đây. 
  + Clone bằng HTTPS: 
{{< highlight sql >}}
  git clone https://gitlab.com/fcj-group/fcj-book-store-backend.git
{{< /highlight >}}

  + Clone bằng HTTPS:
{{< highlight sql >}}
  git clone git@gitlab.com:fcj-group/fcj-book-store-backend.git
{{< /highlight >}}

### Cài đặt K6
Với **Windows**, chạy command với [Windows Package Manager](https://github.com/microsoft/winget-cli):
{{< highlight sql >}}
  winget install k6
{{< /highlight >}}

Hoặc nếu không muốn chạy command bạn có thể tải file .msi [tại đây.](https://dl.k6.io/msi/k6-latest-amd64.msi)

Với hệ điều hành **MacOS, Linux, Ubuntu,** mời bạn tham khảo cách cài đặt cụ thể [tại đây.](https://k6.io/docs/get-started/installation/)

Để kiểm tra thành công hay chưa hãy chạy command:
{{< highlight sql >}}
  k6 version
{{< /highlight >}}

#### Kiểm tra
  + Chạy lệnh k6 với **Terminal** trên **Visual Studio Code**:
{{< highlight sql >}}
  k6 run path/to/your/fike-k6.js
{{< /highlight >}}

  + Kết quả
  
![K6](/Workshop-AWS/images/2.prerequisite/001-k6.png)

Tài liệu tham khảo: [https://k6.io/](https://k6.io/)

