---
title: "Event 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---


# Bài thu hoạch “GenAI-powered App-DB Modernization workshop”

### MỤC ĐÍCH CỦA SỰ KIỆN
Chia sẻ các giải pháp thực tế và best practices trong việc ứng dụng Trí tuệ nhân tạo (AI/LLM) và tối ưu hóa hạ tầng điện toán đám mây đám mây (AWS).
Giới thiệu các mô hình kiến trúc AI tiên tiến (Multi-Agent Systems, Context Engineering, AI Assistants).
Hướng dẫn tối ưu hóa chi phí, tăng cường bảo mật và nâng cao hiệu năng vận hành từ vùng biên (Edge) đến máy chủ gốc (Origin).
Chia sẻ kinh nghiệm thực tế, bài học xương máu từ các dự án Hackathon và quá trình phát triển sản phẩm công nghệ dưới áp lực lớn.
DANH SÁCH DIỄN GIẢ & ĐỘI NGŨ
Vy Lam – Senior Business Systems Analyst tại VPBank.
Đức Đào – Solution Architect tại Cloud Kinetics.
Team VIB – Đội ngũ phát triển dự án UTMorpho tại cuộc thi Lotus Hacks 
Phạm Ng Hải Anh – G-AsiaPacific Vietnam, AWS Community Builder.
Nguyễn Tuấn Thịnh – DevOps Engineer.
Tinh Truong (Trương Tịnh) – Platform Engineer tại GoTymeX.


#### NỘI DUNG NỔI BẬT (TỪ CÁC BÀI THUYẾT TRÌNH)
#### 1. Hệ thống Multi-Agent cấp Doanh nghiệp (Diễn giả: Vy Lam)
Sự bất tương thích cấu hình: Hệ thống chấm điểm tín dụng ngân hàng truyền thống (yêu cầu dữ liệu tài chính 3 năm, tài sản thế chấp) hoàn toàn không phù hợp với thực tế của các Startup (chỉ có dữ liệu vận hành 6-18 tháng, tài sản là IP/con người, dữ liệu phi cấu trúc).
Mô hình Hội đồng tín dụng ảo (Multi-Agent Paradigm): Thay vì dùng 1 Agent duy nhất dễ bị loãng ngữ cảnh, hệ thống phân rã thành nhiều Agent chuyên hóa (Financial Analyst, Market Analyst, Team Evaluator, Risk Assessor, Compliance) kết nối qua giao thức MCP để cùng chấm điểm.
Hiệu quả vượt trội (ROI): Giảm thời gian xử lý hồ sơ từ 2-3 tuần xuống còn 2-4 giờ (nhanh hơn 95%), giảm hơn 90% chi phí vận hành.
Bảo mật cấp doanh nghiệp: Triển khai qua Bedrock AgentCore, Terraform và bắt buộc có Guardrails để bảo vệ dữ liệu nhạy cảm (PII) và chặn Prompt Injection.
#### 2. Bản chất không định hình của cấu hình "Deterministic" LLM (Diễn giả: Đức Đào)
Lầm tưởng về Temperature = 0: Người dùng thường nghĩ đặt T=0 (Greedy Decoding) thì mô hình AI sẽ luôn trả về kết quả giống nhau 100% cho cùng một câu lệnh.
Thực tế nghiên cứu: Không có mô hình lớn nào (GPT-4o, Llama-3, Mixtral...) định hình tuyệt đối ở T=0. Sự sai lệch này do kiến trúc phần cứng GPU, sai số toán học số dấu phẩy động (floating-point) và các thuật toán tối ưu hóa suy luận.
Hậu quả & Khắc phục: T=0 dễ làm mô hình bị kẹt vào các vòng lặp phản hồi. Giải pháp là đặt T=0.1 (tạo một cú hích ngẫu nhiên nhỏ để thoát lặp) kết hợp tăng repeat penalty và thiết kế hệ thống chấp nhận tính xác suất. Bắt buộc đầu ra có cấu trúc (JSON/YAML) bằng tham số hệ thống thay vì chỉ dùng prompt.
#### 3. Nhật ký 36 giờ Hackathon - Xây dựng UTMorpho (Team VIB)
Hành trình từ số 0: Tham gia Lotus Hacks 2026 (Hackathon lớn nhất Việt Nam) với cái đầu rỗng, tìm kiếm ý tưởng từ chính những "nỗi đau" (bực bội) trong công việc hằng ngày để khai sinh ra sản phẩm UTMorpho.
Thách thức thực tế: Áp lực thời gian nghẹt thở, đối mặt với hiện tượng AI tạo tràn lan (Overgeneration), chạm ngưỡng giới hạn Token (Token Limits) và sự kiệt sức (Burnout) của các thành viên ngay trước giờ thuyết trình (Pitch Time).
Bước ngoặt: Nhờ vào việc tập trung tối ưu hóa trải nghiệm chỉnh sửa (Focused Editing Experience) và sự đồng bộ, đồng lòng của toàn đội (Team Sync).
#### 4. Trợ lý AI thân thiện với Amazon Quick (Diễn giả: Hải Anh)
Nỗi đau của Business User: Mất quá nhiều thời gian để thu thập thông tin từ các nguồn phân tán, tốn sức cho các tác vụ lặp đi lặp lại và bị phụ thuộc vào chuyên gia khi cần phân tích các tập dữ liệu chuyên sâu.
Giải pháp Amazon Quick Suite: Không gian hợp nhất cho con người và AI Agent cộng tác. Kết nối hơn 40 nguồn dữ liệu, các mô hình Bedrock và file người dùng để chuyển hóa nhanh nhất từ "nhận thức" sang "hành động".
Ứng dụng thực tế (PM Assistant): Tự động hóa hoàn toàn quy trình lập Biên bản cuộc họp (MoM) $\rightarrow$ Tự động gửi email cho các bên liên quan $\rightarrow$ Tự động lên lịch cuộc họp tiếp theo.
 #### 5. Tối ưu hạ tầng mạng nền tảng với CloudFront (Diễn giả: Tuấn Thịnh)
Nỗi sợ hóa đơn Cloud: Các doanh nghiệp lo lắng chi phí tăng vọt do lưu lượng biến động hoặc bị tấn công DDoS (Usage-based billing).
Giải pháp Gói cước cố định (Fixed-Price Plans): CloudFront giới thiệu các gói tháng cố định (Free, Pro, Business, Premium) giúp kiểm soát chi phí, cam kết không có phí vượt hạn mức và lưu lượng từ các cuộc tấn công bị chặn sẽ không bị tính tiền.
Tối ưu hiệu năng vượt trội: Sử dụng hơn 700 PoPs toàn cầu và cơ chế kết nối bền vững để giảm tải CPU cho máy chủ gốc EC2 từ 5% xuống 1%. Tích hợp HTTP/3 multiplexing giúp tải tài nguyên song song và nén dữ liệu giúp giảm thời gian phản hồi tới 81% (từ 123ms xuống 24ms).
#### 6. Kỹ nghệ ngữ cảnh - Context Is Everything (Diễn giả: Tịnh Trương)
Thông điệp cốt lõi: Mô hình AI hiện nay rất mạnh. Kết quả AI trả về tệ hoặc chung chung phần lớn là do ngữ cảnh đầu vào (input) quá yếu, không phải do mô hình dở.
3 sai lầm kinh điển khi dùng AI:
The "Internet Puller": Nhồi nhét quá nhiều tài liệu, văn bản không lọc vào chat làm loãng thông tin và tốn token.
Nói điều hiển nhiên: Đưa cho AI đoạn code có sẵn rồi lại ra lệnh cấu hình lại chính công nghệ đó thay vì tập trung vào logic cần sửa.
Thiếu mục tiêu và ràng buộc: Đưa ra yêu cầu mơ hồ khiến AI phải tự đoán mò.
Khung ngữ cảnh chuẩn (Simple Context Framework): Trước khi prompt, luôn chuẩn bị đủ 4 yếu tố: Mục tiêu (Goal), Thông tin liên quan (Relevant info), Ràng buộc (Constraints), và Tiêu chí thành công (Success criteria).


#### NHỮNG GÌ HỌC ĐƯỢC
#### Tư Duy Thiết Kế & Phát Triển Ứng Dụng
Business-First Approach: Ý tưởng công nghệ và sản phẩm tốt nhất luôn bắt đầu từ việc giải quyết các bài toán, khó khăn có thật trong thực tế kinh doanh và vận hành hàng ngày, không phải từ việc chạy đua theo công nghệ.
Context Engineering là kỹ năng cốt lõi: Tương lai không phải là cuộc chiến giữa Người vs AI, mà là giữa Người biết cách dùng AI (thông qua quản lý và thiết kế ngữ cảnh tốt) vs Người không biết dùng. Sự dịch chuyển đang đi từ Prompt $\rightarrow$ Context Systems $\rightarrow$ Trí nhớ dài hạn (Memory).
Tư duy thiết kế hệ thống AI Agentic: Khi giải quyết các bài toán phức tạp cho doanh nghiệp, mô hình phối hợp Multi-Agent (nhiều Agent chuyên hóa phối hợp) mang lại độ chính xác, khả năng kiểm định và hiệu quả ROI vượt trội so với một Agent đơn lẻ.
#### Kiến Trúc Kỹ Thuật & Vận Hành Hạ Tầng
Chấp nhận tính xác suất (Probabilistic Mindset): Khi xây dựng ứng dụng với LLM, phải thiết kế hệ thống theo hướng chấp nhận đầu ra có sự biến động (ngay cả ở T=0). Cần bọc logic kiểm tra phía sau và kiểm thử liên tục thay vì tin tưởng tuyệt đối vào tính định hình của mô hình.
Tối ưu hóa từ Vùng Biên (Edge Computing): Sử dụng các giải pháp như CloudFront Function hoặc Lambda@Edge để xử lý logic (chuyển hướng địa lý, kiểm tra bảo mật, đổi URL) ngay tại vùng biên nhằm giảm tải tối đa cho máy chủ gốc và tăng tốc độ phản hồi cho người dùng.
#### ỨNG DỤNG VÀO CÔNG VIỆC
Tối ưu hóa các câu lệnh (Prompting): Áp dụng ngay Simple Context Framework (Xác định rõ Mục tiêu, Thông tin, Ràng buộc, Tiêu chí thành công) vào quy trình làm việc hằng ngày với AI để tăng chất lượng code và tài liệu.
Thiết kế ứng dụng AI Agent: Khi phát triển các tính năng AI phức tạp, chuyển hướng từ thiết kế đơn lẻ sang kiến trúc phân rã nhiệm vụ cho nhiều Agent chuyên trách, đồng thời cấu hình Temperature = 0.1 để tránh lỗi lặp vô hạn.
Nghiên cứu ứng dụng Amazon Quick & Giao thức MCP: Thử nghiệm tích hợp mô hình kết nối công cụ và cơ sở tri thức doanh nghiệp để tự động hóa các quy trình lặp đi lặp lại (như tự động tạo biên bản họp, viết báo cáo).
Tối ưu hạ tầng mạng: Đề xuất cấu hình CDN/CloudFront kết hợp ẩn giấu máy chủ gốc (Origin Cloaking) cho các dự án web để bảo vệ hệ thống khỏi tấn công DDoS và tối ưu hóa chi phí băng thông bằng các gói cước cố định.
#### TRẢI NGHIỆM TRONG EVENT (AWS COMMUNITY DAY / CLOUD AI JOURNEY)
Tham gia chuỗi các phiên trình bày tại sự kiện là một trải nghiệm cực kỳ thực tế và giá trị, giúp tôi kết nối được khoảng cách giữa lý thuyết AI/Hạ tầng và bài toán thực tế của doanh nghiệp.
Học hỏi từ các chuyên gia thực chiến: Được nghe chia sẻ trực tiếp từ các Solution Architect, DevOps Engineer, và BSA đến từ các tổ chức lớn (VPBank, GoTymeX, Cloud Kinetics, G-AsiaPacific), giúp hiểu sâu về cách các doanh nghiệp lớn giải quyết bài toán bảo mật dữ liệu, rủi ro chi phí Cloud và giới hạn của AI.
Trải nghiệm kỹ thuật và góc nhìn đa chiều: Từ những nghiên cứu sâu về phần cứng/GPU ảnh hưởng đến tính định hình của LLM, cho đến những chia sẻ đầy cảm xúc, áp lực và "bài học xương máu" trong 36 giờ sinh tử tại phòng thi Hackathon.
Định hướng rõ ràng cho tương lai: Nhận ra tầm quan trọng của việc làm chủ "Kỹ nghệ ngữ cảnh" (Context Engineering) và tư duy "Doanh nghiệp" khi thiết kế bất kỳ hệ thống AI nào – không chỉ làm cho nó chạy được, mà phải chạy một cách bảo mật, tin cậy và có khả năng mở rộng quy mô.
Một số hình ảnh khi tham gia sự kiện
Thêm các hình ảnh của các bạn tại đây

#### Một số hình ảnh khi tham gia sự kiện
* Thêm các hình ảnh của các bạn tại đây
![alt text](z7866450150269_87bf550e28462644de70351a8524597e.jpg)
![alt text](z7866450137122_fa7ac674224cf3e8b1fe76ae81263462.jpg)
![alt text](z7866450114341_f4f7bf1c450c1fbfc72d663d28be7689.jpg)