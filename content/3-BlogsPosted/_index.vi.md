---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

{{% notice warning %}}  
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Tại đây sẽ là phần liệt kê, giới thiệu các blogs mà các bạn đã đăng trên [AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj). Ví dụ:

### BLOG 1: GIỚI THIỆU SƠ LƯỢC VỀ SESSION POLICIES TRONG AMAZON EKS POD IDENTITY
# Giới Thiệu
Trong bảo mật Kubernetes, việc áp dụng nguyên tắc Least Privilege (Quyền hạn tối thiểu) cho từng Pod luôn là một bài toán đau đầu khi hệ thống phình to. Trước đây, AWS đã mang đến IRSA (IAM Roles for Service Accounts) và gần đây là Amazon EKS Pod Identity để đơn giản hóa việc gán quyền IAM cho Pod.Giờ đây, AWS tiếp tục nâng cấp EKS Pod Identity bằng việc bổ sung tính năng Session Policies. Tính năng này cho phép bạn thu hẹp quyền hạn IAM một cách linh hoạt và chính xác cho từng Pod cụ thể mà không cần phải tạo ra hàng tá IAM Roles riêng biệt.
# Bài Toán Cũ:
 Sự Bùng Nổ Của IAM RolesTrước khi có Session Policies, nếu bạn có 100 ứng dụng (Pod) khác nhau cần truy cập vào 100 thư mục (S3 bucket) riêng biệt, bạn sẽ phải:Tạo ra 100 IAM Roles khác nhau.Quản lý và duy trì hàng trăm chính sách bảo mật (IAM Policies) đi kèm.Quy trình này gây ra tình trạng IAM Role Explosion (Bùng nổ IAM Role), làm tăng chi phí quản trị và rất dễ dẫn đến sai sót cấu hình bảo mật ở quy mô lớn.
 # Giải Pháp Mới: 
 Thu Hẹp Quyền Linh Hoạt Với Session PoliciesVới tính năng mới, bạn chỉ cần tạo một IAM Role dùng chung (ví dụ: GameDataDataWriter) sở hữu quyền hạn rộng hơn một chút trên dịch vụ (ví dụ: Quyền ghi vào toàn bộ S3 Buckets của dự án).Khi cấu hình EKS Pod Identity Association cho một Pod cụ thể, bạn có thể đính kèm một Session Policy (Chính sách phiên). Chính sách này hoạt động như một màng lọc (filter):Nó sẽ giao cắt (intersect) với IAM Role gốc.Pod đó sẽ chỉ có quyền thực thi các hành động được định nghĩa trong cả IAM Role lẫn Session Policy.Kết quả: Từ một IAM Role duy nhất, bạn có thể biến hóa ra hàng trăm phiên làm việc với quyền hạn tối thiểu khác nhau cho từng Pod, giúp hệ thống EKS gọn gàng và bảo mật hơn rất nhiều.
 ### BLOG 2: ĐI SÂU VÀO KIẾN TRÚC VÀ CƠ CHẾ HOẠT ĐỘNG
 # Cách Thức Vận Hành Của Session PoliciesĐể hiểu cách Session Policies hoạt động trong EKS Pod Identity, chúng ta cần nhìn vào luồng xử lý nhận diện (Credential Flow) khi một Pod gửi yêu cầu đến dịch vụ AWS:
 Định nghĩa IAM Role gốc: Bạn tạo một IAM Role với quyền hạn tổng quát cần thiết cho nhóm ứng dụng.
 Cấu hình Pod Identity với Session Policy: Khi tạo cấu hình liên kết (Association) cho Pod, bạn truyền thêm một chính sách nội dung (Inline hoặc Managed Policy) làm Session Policy.
 Pod yêu cầu Token bảo mật: Khi ứng dụng trong Pod gọi AWS SDK, EKS Pod Identity Agent trên Worker Node sẽ gửi yêu cầu lấy thông tin xác thực (AssumeRole) đến AWS STS.
 AWS STS áp dụng màng lọc: AWS STS sẽ lấy IAM Role gốc và áp dụng Session Policy được chỉ định để tạo ra một bộ Temporary Credentials (chứng chỉ tạm thời) độc nhất cho Pod đó.
 # Cơ Chế Giao Cắt Quyền Hạn (Policy Intersection)
 Một điểm cực kỳ quan trọng cần lưu ý là Session Policy không thể mở rộng quyền hạn vượt quá IAM Role gốc. Nó chỉ có tác dụng thu hẹp quyền hạn.
 $$Quy\ \hat{e}n\ th\subset \!c\ t\ \acute{e}\ = Quy\ \hat{e}n\ IAM\ Role\ \cap \ Quy\ \hat{e}n\ Session\ Policy$$
 Nếu IAM Role cho phép truy cập Bucket-A và Bucket-B.Session Policy chỉ cho phép truy cập Bucket-A.Kết quả: Pod đó chỉ có thể truy cập Bucket-A. Nếu Pod cố gắng gọi đến Bucket-B, yêu cầu sẽ bị từ chối ngay lập tức (Access Denied).
 ### BLOG 3: LỢI ÍCH THỰC TẾ VÀ KHẢ NĂNG ỨNG DỤNG TRONG GAME STUDIO
 # Những Lợi Ích Vượt Trội Cho Môi Trường Doanh Nghiệp
 Việc áp dụng Session Policies mang lại những giá trị thực tế rất lớn cho các đội ngũ vận hành Cloud (Cloud Platform Teams):
 Tối ưu hóa quản trị hạ tầng (Scale cleanly): Giảm thiểu số lượng IAM Roles cần tạo và quản lý trên AWS Console. Hệ thống IAM của bạn sẽ sạch sẽ hơn.
 Tăng cường tính bảo mật (Enhanced Security): Giảm thiểu rủi ro khi một Pod bị tấn công mạng. Kẻ tấn công không thể leo thang đặc quyền sang các tài nguyên khác vì Session Policy đã giới hạn chặt chẽ phạm vi hoạt động của Pod đó.
 Tự động hóa linh hoạt: Phù hợp hoàn hảo với các pipeline CI/CD bằng Terraform hoặc các công cụ GitOps như ArgoCD, cho phép cấu hình quyền động theo từng môi trường dev/staging/prod.
 # Case Study: Ứng Dụng Trong Hệ Thống Game Server (EKS)
 Hãy tưởng tượng studio game của bạn đang vận hành một cụm Amazon EKS để chạy các Dedicated Game Server cho nhiều trận đấu (Match) cùng lúc:
 Thách thức: Mỗi Game Server sau khi kết thúc trận đấu cần upload file log và replay của trận đó lên một folder riêng tư trên Amazon S3 (s3://game-replays/match-id-*). Bạn không thể tạo trước hàng ngàn IAM Role cho hàng ngàn trận đấu được khởi tạo liên tục.Giải pháp với Session Policy: Bạn chỉ cần 1 IAM Role duy nhất có quyền ghi vào bucket s3://game-replays/. Khi hệ thống tạo Pod cho trận đấu match-123, EKS Pod Identity sẽ tự động đính kèm một Session Policy chỉ cho phép ghi vào đường dẫn chính xác: s3://game-replays/match-123/*.
 Kết luận: Session Policies trong Amazon EKS Pod Identity chính là mảnh ghép hoàn hảo giúp các studio game vừa đảm bảo tốc độ triển khai nhanh chóng, vừa giữ vững tiêu chuẩn bảo mật tối cao của AWS Best Practices.