---
title : "Tạo SAM pipeline"
date :  "2025-08-11" 
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

#### Chuẩn bị
Trong bước này, chúng ta sẽ tạo các vai trò IAM cho **CodePipeline - Giai đoạn triển khai** và **CodeBuild.**

{{% notice warning %}}
  Cảnh báo Vai trò được cấu hình với bảo mật tối thiểu, chỉ phù hợp cho môi trường workshop.
{{% /notice %}}

1. Tạo vai trò **CodePipeline - Giai đoạn triển khai.**
    + Mở [AWS IAM console](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1), sau đó nhấp vào **Roles** trên menu bên trái.
    + Nhấp vào nút **Create role.**
    ![IAM](/Workshop-AWS/images/3.cicd/iam-001.png)

   + Tại trang **Step 1: Select trusted entity.**
      + Chọn **AWS service** tại **Trusted entity type.**
      + Nhập `CloudFormation` tại **Service or use case** và chọn **CloudFormation** tại **Use case.**
      + Sau đó nhấp vào nút **Next**.
      ![IAM](/Workshop-AWS/images/3.cicd/iam-002.png)

   + Tại trang **Step 2: Add permissions.**
      + Nhập `AdministratorAccess` tại hộp **Search**.
      + Chọn chính sách **AdministratorAccess**
      + Sau đó nhấp vào nút **Next**.
      ![IAM](/Workshop-AWS/images/3.cicd/iam-003.png)

   + Tại trang **Step 3: Name, review, and create.**
      + Nhập `fcjCodePipelineDeployStageRole` tại **Role name.**
      ![IAM](/Workshop-AWS/images/3.cicd/iam-004.png)

      + Cuộn xuống và nhấp vào nút **Create role.**
      ![IAM](/Workshop-AWS/images/3.cicd/iam-005.png)

2. Tạo vai trò **CodeBuild**.
    + Mở [AWS IAM console](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1), sau đó nhấp vào **Roles** trên menu bên trái.
    + Nhấp vào nút **Create role.**
    ![IAM](/Workshop-AWS/images/3.cicd/iam-006.png)

   + Tại trang **Step 1: Select trusted entity.**
      + Chọn **AWS service** tại **Trusted entity type.**
      + Nhập `CodeBuild ` tại **Service or use case** và chọn **CodeBuild** tại **Use case.**
      + Sau đó nhấp vào nút **Next**.
      ![IAM](/Workshop-AWS/images/3.cicd/iam-007.png)

   + Tại trang **Step 2: Add permissions.**
      + Nhập `AdministratorAccess` tại hộp **Search**.
      + Chọn chính sách **AdministratorAccess**
      + Sau đó nhấp vào nút **Next**.
      ![IAM](/Workshop-AWS/images/3.cicd/iam-008.png)

   + Tại trang **Step 3: Name, review, and create.**
      + Nhập `fcjCodeBuildRole ` tại **Role name.**
      ![IAM](/Workshop-AWS/images/3.cicd/iam-009.png)

      + Cuộn xuống và nhấp vào nút **Create role.**
      ![IAM](/Workshop-AWS/images/3.cicd/iam-010.png)

#### Tạo pipeline
1. Mở [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    + Nhấp vào **Pipelines** trên menu bên trái.
    + Nhấp vào nút **Create pipeline.**
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-001.png)

2. Tại trang **Step 1: Choose creation option.**
    + Chọn **Build custom pipeline** tại **Creation options.**
    + Sau đó nhấp vào nút **Next**.
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-002.png)

3. Tại trang **Step 2: Choose pipeline settings.**
    + Nhập `fcjBookStorePipeline` tại **Pipeline name.**
    + Chọn **Queued** tại **Execution mode.**
    + Chọn **New service** role tại **Service role.**
    + Nhập `AWSCodePipelineServiceRole-us-east-1-fcjBookStorePipeline` tại **Role name.**
    + Sau đó nhấp vào nút **Next**.
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-003.png)

4. Tại trang Step 3: Add source stage.
    + Chọn **Gitlab** tại **Source provider.**
    + Nhấp vào nút **Connect to Gitlab.**
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-004.png)

    + Tại trang **Create a connection** ở tab trình duyệt mới vừa mở.
      + Nhập `fcjBookStoreGitlabConnection` tại **Connection name.**
      + Nhấp vào nút **Connect to Gitlab.**
      ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-005.png)

      + Sau khi đăng nhập thành công vào Gitlab, nhấp vào nút **Connect**.
      ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-006.png)
    
    + Kiểm tra xem kết nối **Gitlab** có thành công không.
    + Nhập `fcj-ws/fcj-book-store-backend` tại **Repository name.**
    + Nhập `master` tại **Default branch.**
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-007.png)

    + Cuộn xuống cuối trang và nhấp vào nút **Next**.
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-008.png)

5. Tại trang **Step 4: Add build stage.**
    + Chọn **Other build providers** tại **Build provider.**
    + Chọn **AWS CodeBuild.**
    + Nhấp vào nút **Create project.**
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-009.png)

    + Tại trang **Create build project** ở tab trình duyệt mới vừa mở.
      + Nhập `fcjBookStoreBuildProject` tại **Project name.**
      ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-010.png)

      + Cuộn xuống, chọn **Ubuntu** tại **Operating system.**
      + Chọn **Existing service role** tại **Service role.**
      + Chọn **fcjCodeBuildRole** tại **Role ARN.**
      ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-011.png)

      + Cuộn xuống cuối trang, chọn **Use a buildspec file** tại **Build specifications.**
      + Nhấp vào nút **Continue to CodePipeline.**
      ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-012.png)
    
    + Chọn **fcjBookStoreBuildProject** tại **Project name.**
    + Để mặc định và nhấp vào nút **Next**.
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-013.png)

6. Tại trang **Step 5: Add test stage.**
    + Nhấp vào nút **Skip test stage.**
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-014.png)

7. Tại trang **Step 6: Add deploy stage.**
    + Chọn **AWS CloudFormation** tại **Deploy provider.**
    + Chọn **BuildArtifact** tại **Input artifacts.**
    + Chọn **Create or update a stack** tại **Action mode.**
    + Nhập `fcj-book-store` tại **Stack name.**
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-015.png)

    + Cuộn xuống, chọn **BuildArtifact** tại **Artifact name.**
    + Nhập `packaged.yaml` tại **File name.**
    + Chọn **CAPABILITY_IAM, CAPABILITY_NAMED_IAM** và **CAPABILITY_AUTO_EXPAND** tại **Capabilities - optional.**
    + Chọn **fcjCodePipelineDeployStageRole** tại **Role name.**
    + Nhấp vào nút **Next**.
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-016.png)

8. Tại trang **Step 7: Review.**
    + Cuộn xuống và nhấp vào nút **Create pipeline.**
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-017.png)

#### Kiểm tra pipeline
1. Mở [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    + Nhấp vào **Pipelines** trên menu bên trái.
    + Chọn pipeline **fcjBookStorePipeline**.
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-018.png)

2. Tại trang **fcjBookStorePipeline**.
    + Nhấp vào khung **CodeBuild.**
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-019.png)

3. Kết quả   
    + **CodePipeline** + **Codebuild** đã tự động chạy kiểm thử tải **K6** từ file `buildspec.yml` trên **GitLab**
    ![Pipeline](/Workshop-AWS/images/3.cicd/pipeline-020.png)    

