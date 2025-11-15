# 🤖 Chatbot Hỗ Trợ Sinh Viên – Đại Học Cần Thơ

---

## 🌟 Giới thiệu

Dự án **Chatbot Giáo Dục** được phát triển bởi **Nhóm 19**

👩‍💻 Thành viên Nhóm 19:

Họ và Tên	MSSV -	Vai trò

Nguyễn Đặng Minh Hoàng M5125003 – Xử lý dữ liệu & tích hợp

Trầm Thanh Phú M5125021 - Tối ưu hội thoại & huấn luyện mô hình

Danh Thế Anh M5125001

Nguyễn Minh Thạnh M5125012 - Slide báo cáo

Với mục tiêu xây dựng một **trợ lý ảo thân thiện**, giúp sinh viên tra cứu nhanh thông tin học vụ, quy định, và hỗ trợ định hướng học tập.

Chatbot sử dụng **ngôn ngữ tự nhiên (NLP)** và công nghệ **LangChain + Ollama**, cho phép truy xuất thông tin từ cơ sở tri thức tùy chỉnh (`kien_thuc_giao_duc.txt`) và phản hồi chính xác bằng tiếng Việt.

---

## 🧠 Tính năng nổi bật

✅ **Tra cứu thông tin học vụ**
- Xem điểm, lịch học, lịch thi, tín chỉ, học phí.
- Truy cập nhanh:
  - 📘 Cổng xem điểm: [https://qldt.ctu.edu.vn](https://qldt.ctu.edu.vn)
  - 🧾 Đăng ký học phần: [https://dkmh.ctu.edu.vn](https://dkmh.ctu.edu.vn)
  - 📅 Lịch học & thi: [https://thisinh.ctu.edu.vn](https://thisinh.ctu.edu.vn)

✅ **Tư vấn học tập & quy chế**
- Quy định học vụ, bảo lưu, học bổng, xét tốt nghiệp.
- Mẹo học tập, kỹ năng mềm và hướng dẫn tra cứu tài liệu.

✅ **Thông tin hành chính**
- Liên hệ các phòng ban: Đào tạo, CTSV, Ký túc xá, IT Support.
- Tra cứu biểu mẫu hành chính, lịch nghỉ lễ, hỗ trợ kỹ thuật.

✅ **Không trả lời ngoài phạm vi**
Chatbot được giới hạn trong chủ đề **học sinh – sinh viên**, không phản hồi các câu hỏi về thời sự, giải trí, chính trị hoặc công nghệ ngoài học vụ.

---

## 📂 Cấu trúc thư mục dự án

```bash
chatbot_giao_duc/
│
├── data/
│   ├── kien_thuc_giao_duc.txt      # Tập tin chứa kiến thức giáo dục & thông tin trường
│
├── app.py                          # File chính để chạy chatbot
├── requirements.txt                # Thư viện cần thiết
├── README.md                       # Mô tả dự án
└── utils/                          # Các hàm hỗ trợ NLP, xử lý dữ liệu, v.v.
```
🤖 Chatbot Học vụ CTU – Hệ thống RAG với LangChain + Ollama
1. Giới thiệu dự án

Dự án này xây dựng một chatbot hỗ trợ học vụ cho sinh viên Trường Đại học Cần Thơ (CTU). Chatbot hoạt động dựa trên kiến trúc RAG (Retrieval-Augmented Generation), kết hợp mô hình ngôn ngữ lớn (LLM) chạy qua Ollama, trích xuất dữ liệu bằng LangChain và lưu trữ/truy vấn dữ liệu bằng ChromaDB.
Mục tiêu của chatbot: trả lời câu hỏi học vụ, cung cấp link chính thức, hạn chế bịa đặt nhờ sử dụng dữ liệu RAG, và phản hồi ngắn gọn rõ ràng.

2. Kiến trúc hệ thống

Luồng hoạt động: Người dùng → Câu hỏi → RAG → Truy xuất dữ liệu → LLM → Trả lời hoàn chỉnh.
Các thành phần chính:

TextLoader: tải dữ liệu từ file kien_thuc_giao_duc.txt

TextSplitter: chia nhỏ dữ liệu thành chunk

Embedding: chuyển chunk thành vector bằng nomic-embed-text

ChromaDB: lưu embeddings để truy vấn nhanh

LLM (llama3.1:8b): tạo câu trả lời

Prompt tùy chỉnh: đảm bảo output đúng dạng yêu cầu

3. Chức năng chính

Trả lời các câu hỏi học vụ: đăng ký môn học, lịch thi, lịch học, xem điểm

Cung cấp đầy đủ link chính thức của CTU

Dẫn nguồn dữ liệu từ file RAG

Trả lời theo format gọn (3–6 câu)

Hạn chế bịa đặt thông tin khi dữ liệu không có

4. Công nghệ sử dụng

Python 3.9+

LangChain & LangChain Community

Ollama

ChromaDB

Nomic Embedding

PromptTemplate

5. Hướng dẫn cài đặt
Bước 1 – Cài đặt Ollama

Tải và cài đặt tại: https://ollama.com/download

Sau khi cài, tải các model cần dùng:

ollama pull llama3.1:8b

ollama pull nomic-embed-text

Kiểm tra: ollama list.

Bước 2 – Cài đặt thư viện Python

Chạy lệnh sau:
pip install langchain langchain-community langchain-core langchain-ollama chromadb python-pptx pypandoc

Bước 3 – Chuẩn bị dữ liệu RAG

Tạo file kien_thuc_giao_duc.txt chứa:

Thông tin học vụ CTU

Quy chế đào tạo

Thao tác đăng ký môn

Liên hệ các phòng ban

Câu hỏi – đáp phổ biến

Bước 4 – Chạy chương trình

Sử dụng lệnh:
python main.py
Nếu chạy thành công bạn sẽ thấy: “Chatbot CTU đã sẵn sàng!”.

6. Cách sử dụng

Gõ câu hỏi bất kỳ về học vụ:

“Làm sao đăng ký môn học?”

“Tra lịch thi ở đâu?”

“Số điện thoại phòng đào tạo?”

“Xem điểm như thế nào?”

Chatbot sẽ:

Truy xuất RAG

Ghép vào prompt

Trả lời có link, có nguồn, có mức độ tin cậy

7. Link – thông tin học vụ CTU

Đăng ký môn học: https://dkmhfe.ctu.edu.vn

Xem điểm / lịch thi / lịch học: https://htql.ctu.edu.vn

Hỗ trợ kỹ thuật: https://helpdesk.ctu.edu.vn

Phòng Đào tạo: pdt@ctu.edu.vn
 – 0292 383 1156

Phòng Công tác sinh viên: pctsv@ctu.edu.vn
 – 0292 387 2177

8. Ghi chú

Dự án chạy 100% offline, bảo mật cao

Có thể mở rộng thành chatbot web bằng Streamlit hoặc FastAPI

Có thể thêm nhiều file dữ liệu học vụ khác

9. Bản quyền

Dự án nhằm mục đích học tập – báo cáo môn học, không phải sản phẩm chính thức của CTU.
