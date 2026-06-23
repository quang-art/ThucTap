---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# BÁO CÁO TỔNG HỢP MEETUP & WORKSHOP
### Mục Đích Của Sự Kiện

-Mục Đích Của Sự Kiện
Chia sẻ best practices trong thiết kế ứng dụng hiện đại: Cập nhật các xu hướng chuyển dịch kiến trúc ứng dụng từ Legacy sang Cloud-native nhằm tối ưu hiệu suất, tăng tính an ninh và giảm thiểu chi phí vận hành cho doanh nghiệp.

Giới thiệu phương pháp DDD và event-driven architecture: Định hướng tư duy tiếp cận hệ thống từ lõi nghiệp vụ (Business-first), hướng dẫn cách phân rã microservices thông qua Event Storming và xây dựng hệ thống giảm liên kết chéo (Loose coupling).

Hướng dẫn lựa chọn compute services phù hợp: Phân tích dải quang phổ hạ tầng tính toán (Compute spectrum) từ máy ảo VM (EC2), Container (ECS/Fargate) đến Serverless (AWS Lambda) giúp kỹ sư hiểu rõ các tiêu chí đánh đổi (trade-offs) để áp dụng chính xác cho từng use case.

Giới thiệu công cụ AI hỗ trợ development lifecycle: Trải nghiệm thực tế năng lực của Amazon Q Developer trong việc tự động hóa vòng đời phát triển phần mềm (SDLC), từ lập kế hoạch, nâng cấp mã nguồn tự động cho đến bảo trì hệ thống nhằm bứt phá hiệu suất (boost productivity).

Định hình lộ trình phát triển và tư duy của thế hệ kỹ sư mới: Làm rõ bức tranh thực tế về công việc của một DevOps Engineer hay Data Analytics Engineer; định hướng lộ trình nâng cấp năng lực bản thân từ người thực thi (Follower) tiến lên người giải quyết bài toán cốt lõi (Problem Solver) và tư duy toàn cảnh (System Thinker).

Lan tỏa văn hóa làm việc tiên tiến tại các tập đoàn công nghệ toàn cầu: Giới thiệu các giá trị văn hóa doanh nghiệp hiện đại như tư duy No-Blame Post-Mortem (không đổ lỗi khi xảy ra sự cố hệ thống) và quy trình tuyển dụng chuẩn hóa tại các doanh nghiệp MNCs, từ đó thu hẹp khoảng cách giữa môi trường học thuật và thực tế ngành công nghiệp.
# Danh Sách Diễn Giản & Chủ Đề Chia Sẻ
Đinh Trung Kiên - Nguyễn Minh Thọ, A scalable URL shortening service on AWS
Đạt Phạm - Cường Nguyễn , Câu chuyện thực tế đến vắn hóa tập đoàn đa quốc gia
SA, Serverless Amazon Web Services
Danh Hoàng Hiếu Nghị, From First Cloud AI Journey to AWS Partner 
Trong H. Truong (Trọng Trương) - DevOps Engineer @ Endava Vietnam (Chủ đề: What does a DevOps Engineer really do?)   
  # Nội Dung Nổi Bật
  # 1. Ảnh hưởng tiêu cực của kiến trúc ứng dụng cũ
  Tốc độ release chậm: Quy trình cồng kềnh kéo dài thời gian ra mắt sản phẩm, dẫn đến mất doanh thu và bỏ lỡ cơ hội cạnh tranh.
  Hoạt động kém hiệu quả: Gây lãng phí năng suất nhân sự và tốn kém chi phí vận hành, bảo trì.
  Rủi ro bảo mật: Không đáp ứng được các tiêu chuẩn an ninh hiện đại, tăng nguy cơ mất an toàn thông tin và suy giảm uy tín doanh nghiệp.
  # 2. Chuyển đổi sang kiến trúc Microservice & Quy trình Domain-Driven Design (DDD)
  Hệ thống Modular độc lập: Tách biệt ứng dụng thành các dịch vụ nhỏ gọn, giao tiếp bất đồng bộ qua sự kiện (Event-driven) dựa trên 3 trụ cột: Quản lý hàng đợi (Queue Management), Chiến lược bộ nhớ đệm (Caching Strategy), và Xử lý thông điệp linh hoạt (Message Handling).
  Quy trình 4 bước của DDD: Xác định sự kiện nghiệp vụ (Domain events) $\rightarrow$ Sắp xếp dòng thời gian $\rightarrow$ Định danh tác nhân (Identify actors) $\rightarrow$ Khoanh vùng ngữ cảnh (Bounded contexts).
  Context Mapping: Áp dụng 7 patterns để tích hợp các bounded contexts một cách mượt mà thông qua case study thực tế từ mô hình nhà sách (bookstore).
  # 3. Event-Driven Architecture & Mô hình hạ tầng Compute Evolution
  3 Integration Patterns cốt lõi: Publish/Subscribe (Pub/Sub), Point-to-point, và Streaming để xây dựng hệ thống Loose coupling (giảm phụ thuộc chéo), tăng tính mở rộng (scalability) và khả năng chịu lỗi (resilience).
  Sự tiến hóa hạ tầng (Shared Responsibility Model): Dịch chuyển từ máy ảo truyền thống EC2 $\rightarrow$ Containers (ECS/Fargate) $\rightarrow$ Serverless (AWS Lambda). Serverless đem lại lợi ích vượt trội: không cần quản lý máy chủ, tự động co giãn theo lưu lượng (auto-scaling) và tối ưu hóa chi phí dựa trên giá trị sử dụng thực tế (pay-for-value).
  Amazon Q Developer: Trợ lý AI hỗ trợ tự động hóa toàn bộ vòng đời phát triển phần mềm (SDLC). Công cụ này giúp hiện đại hóa mã nguồn (Java upgrade, .NET modernization) và kích hoạt các AWS Transform agents để di trú hệ thống tự động (VMware, Mainframe).
  # 4. Vai trò thực tế của DevOps & Lộ trình phát triển kỹ năng
  Bản chất công việc DevOps: Xây dựng đường ống CI/CD, Quản lý hạ tầng dạng mã (IaC), triển khai Container & K8s, tích hợp Cloud Providers (AWS, Azure) và giám sát hệ thống (Logging/Monitoring). DevOps thực tế không phải là "người hùng cứu hỏa" lúc nửa đêm mà là người tối ưu hóa hệ thống để ngăn chặn sự cố.  
  Lộ trình học tập (DevOps Fundamentals): - Nắm vững gốc rễ: Hệ điều hành Linux, kiến thức mạng cơ bản (Networking). 
   Ngôn ngữ lập trình: Python, Golang.  
   Công cụ quản lý mã nguồn và ảo hóa: Git, CI/CD, Containers (Docker).  
   Thực hành thực chiến: Triển khai dự án nhỏ, cấu hình biến môi trường, tự làm hỏng hệ thống và tự tìm cách sửa lỗi.
#  5. Công việc Data Analytics Engineer & Văn hóa làm việc toàn cầu (MNCs)
Thực tế công việc theo Domain: - Tại Kamereo: Xây dựng báo cáo vận hành định kỳ; thiết kế Dashboard giám sát xu hướng và phát hiện bất thường để hỗ trợ ra quyết định kinh doanh. 
 Tại Colgate-Palmolive: Phân tích dữ liệu máy móc, thiết bị IoT trong nhà máy nhằm tối ưu hóa chi phí sản xuất và thúc đẩy các sáng kiến chuyển đổi số.  
 Bộ kỹ năng cốt lõi: Tư duy phản biện (Critical thinking), kỹ năng giao tiếp, giải quyết bài toán gốc rễ, và kỹ năng kể chuyện bằng dữ liệu (Data storytelling) thông qua các chỉ số vận hành (GMV, Fulfillment cost, Fill rate...).  
 Mô hình phát triển năng lực cá nhân: Dịch chuyển qua 5 cấp độ: Follower (Người thực thi) $\rightarrow$ Learner (Người học chủ động) $\rightarrow$ Problem Solver (Người giải quyết vấn đề) $\rightarrow$ System Thinker (Tư duy hệ thống) $\rightarrow$ Super Star (Người dẫn dắt/xây dựng tầm nhìn).
   Văn hóa doanh nghiệp tiến bộ tại các tập đoàn lớn: - Văn hóa No-Blame Post-Mortem: Khi xảy ra sự cố nghiêm trọng, đội ngũ kỹ sư tập trung phân tích nguyên nhân gốc rễ để nâng cấp hệ thống, tuyệt đối không đổ lỗi cho cá nhân.  Văn hóa Caring & Inclusive: Tôn trọng sự đa dạng, lấy con người làm trung tâm của mọi sự phát triển. 
   # Những Gì Học Được
   # Tư Duy Thiết Kế & Định Hướng
   Business-first approach: Mọi kiến trúc công nghệ đều phải bắt nguồn và phục vụ cho nhu cầu thực tế của domain kinh doanh.
   Ubiquitous language: Tầm quan trọng của việc đồng bộ thuật ngữ, xây dựng ngôn ngữ chung giữa đội ngũ nghiệp vụ (Business) và đội ngũ kỹ thuật (Tech teams) để tránh hiểu lầm.
   Wakon Yosai & Triết lý "Đúng Việc": Học hỏi, làm chủ kỹ nghệ tiên tiến của thế giới nhưng luôn giữ vững tư duy cốt lõi để nâng cấp bản thân thành một "Problem Solver" thực thụ. 
   # Kiến Trúc & Kỹ Thuật Hệ Thống
   Sử dụng thành thạo kỹ thuật Event storming để mô hình hóa quy trình phức tạp thành chuỗi Domain events.
   Thấu hiểu sự đánh đổi (trade-offs) để lựa chọn đúng mô hình giao tiếp (đồng bộ vs bất đồng bộ) và mô hình tính toán phù hợp trên dải quang phổ (Compute spectrum) từ VM, Container đến Serverless.
   Hiểu sâu về triết lý DevOps: "Công cụ có thể thay đổi liên tục, nhưng kiến thức nền tảng (Fundamentals) sẽ ở lại mãi mãi". Tận dụng AI để đòn bẩy hiệu suất chứ không phụ thuộc làm lười tư duy.
 # Chiến Lược Hiện Đại Hóa
 Hiện đại hóa hệ thống phải là một lộ trình từng bước (Phased approach), sử dụng bộ khung 7Rs framework để phân tích đặc tính của từng ứng dụng trước khi dịch chuyển.
 Mọi sự chuyển đổi cần được đo lường cụ thể qua hai chỉ số: Giảm thiểu chi phí (Cost reduction) và Độ linh hoạt của doanh nghiệp (Business agility).
 # Ứng Dụng Vào Công Việc
 Triển khai DDD & Event Storming: Tổ chức các buổi thảo luận chung (Event storming sessions) với nhóm vận hành/kinh doanh để chuẩn hóa "ngôn ngữ chung" (Ubiquitous language) cho dự án hiện tại.
 Tái cấu trúc hệ thống (Refactor Microservices): Sử dụng các vùng ngữ cảnh (Bounded contexts) đã học để vạch rõ ranh giới giữa các dịch vụ, giảm thiểu sự phụ thuộc chéo (Coupling).
 Tích hợp Event-driven Patterns: Lên kế hoạch thay thế dần các cuộc gọi đồng bộ (Sync) bằng cơ chế xếp hàng tin nhắn bất đồng bộ (Async messaging) nhằm tăng tính chịu lỗi cho hệ thống.
 Thử nghiệm Serverless: Lựa chọn một vài tính năng/use case độc lập phù hợp để chạy pilot trên AWS Lambda nhằm tối ưu chi phí hạ tầng.
 Ứng dụng AI trợ lý: Tích hợp Amazon Q Developer vào quy trình viết và review code hàng ngày để nâng cấp hiệu suất phát triển phần mềm (SDLC automation).
 Thay đổi tư duy làm việc cá nhân: Áp dụng mô hình phát triển cá nhân từ "Follower" chủ động chuyển mình thành "Problem Solver"; rèn luyện thói quen đặt câu hỏi "Tại sao" (Why) trước khi đi tìm câu trả lời "Làm thế nào" (How) khi đối mặt với các bài toán hệ thống.  
 # Trải Nghiệm Trong Sự Kiện
 Tham gia workshop “GenAI-powered App-DB Modernization” và chuỗi chia sẻ công nghệ là một trải nghiệm vô cùng giá trị, mang lại cho tôi góc nhìn toàn cảnh về xu hướng công nghệ hiện đại.
 Học hỏi từ các diễn giả đầu ngành
 Được lắng nghe những chia sẻ, bài học "xương máu" từ các chuyên gia đến từ AWS, Endava Việt Nam và các tập đoàn đa quốc gia lớn.  
 Các case study thực tế từ việc xây dựng Dashboard quản lý dữ liệu tại Kamereo hay tối ưu hệ thống sản xuất tại Colgate-Palmolive giúp tôi dễ dàng hình dung lý thuyết khi đưa vào thực tế doanh nghiệp.
 #  Trải nghiệm kỹ thuật & văn hóa thực tế
 Hiểu được bức tranh toàn cảnh về nhu cầu tuyển dụng công nghệ tại Việt Nam, các quy trình phỏng vấn chuẩn hóa (Sàng lọc ATS, Test năng lực, Phỏng vấn chuyên môn qua mô hình STAR).  
 Ấn tượng sâu sắc với tư duy văn hóa No-Blame Post-Mortem. Trải nghiệm này giúp tôi thay đổi cách nhìn nhận về lỗi hệ thống: nhìn nhận lỗi là cơ hội để cải tiến kiến trúc thay vì áp lực đổ lỗi cho cá nhân. 
 #  Mở rộng mạng lưới kết nối (Networking)
 Sự kiện tạo điều kiện giao lưu, kết nối trực tiếp với cộng đồng AWS Community Builders, AWS Student Builders và các kỹ sư phần mềm, kỹ sư dữ liệu trong ngành.  
 Các cuộc thảo luận mở giúp tôi nâng cao tư duy hệ thống (System Thinker), hiểu rõ mối liên kết chéo giữa các bộ phận Tech và Business để phối hợp giải quyết các bài toán thực tế phát sinh một cách hiệu quả lâu dài.
#### Một số hình ảnh khi tham gia sự kiện
* Thêm các hình ảnh của các bạn tại đây
> Tổng thể, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp tôi thay đổi cách tư duy về thiết kế ứng dụng, hiện đại hóa hệ thống và phối hợp hiệu quả hơn giữa các team.
