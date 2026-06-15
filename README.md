       1 # CareerPulse AI
       2
       3 Hệ thống so khớp CV và tìm kiếm công việc thông minh sử dụng kỹ thuật **RAG (Retrieval-Augmented
         Generation)** kết hợp với mô hình ngôn ngữ lớn **Gemini** của Google và cơ sở dữ liệu vector **Qdrant**.
       4
       5 ## 🚀 Tính năng chính
       6
       7 - **Xử lý CV PDF**: Tự động trích xuất văn bản từ các tệp CV định dạng PDF.
       8 - **Tìm kiếm công việc thông minh**: Sử dụng Vector Search để tìm ra các công việc phù hợp nhất với kỹ năng
         và kinh nghiệm trong CV từ cơ sở dữ liệu.
       9 - **Tư vấn cải thiện CV**: Phân tích sự thiếu hụt giữa CV và yêu cầu công việc để đưa ra lời khuyên hữu ích
         cho ứng viên.
      10 - **Hỏi đáp về công việc (Q&A)**: Cho phép người dùng đặt câu hỏi liên quan đến CV và các công việc được
         gợi ý.
      11 - **Giao diện web trực quan**: Xây dựng trên nền tảng Flask, dễ dàng sử dụng và tương tác.
      12
      13 ## 🏗️ Cấu trúc dự án
      14
      15 ```text
      16 web/
      17 ├── app.py              # File chạy chính của ứng dụng Flask
      18 ├── core/               # Chứa logic xử lý cốt lõi
      19 │   ├── data.py         # Xử lý PDF (PDFProcessor)
      20 │   ├── embedding_que.py # Tạo vector embedding từ văn bản
      21 │   ├── retriever.py    # Truy vấn công việc từ Qdrant
      22 │   └── rag.py          # Generator câu trả lời sử dụng Gemini
      23 ├── api/                # Các module API bổ trợ
      24 ├── data/               # Chứa dữ liệu công việc (JSON)
      25 ├── templates/          # Giao diện người dùng (HTML/CSS/JS)
      26 ├── uploads/            # Thư mục lưu trữ CV tạm thời
      27 └── requirements.txt    # Danh sách các thư viện cần thiết
      28 ```
      29
      30 ## 🛠️ Công nghệ sử dụng
      31
      32 - **Backend**: Python, Flask
      33 - **LLM**: Google Gemini API (Model: `gemini-2.5-flash-lite`)
      34 - **Embeddings**: Google Gemini Embedding API (Model: `gemini-embedding-exp-03-07`)
      35 - **Vector Database**: Qdrant Cloud
      36 - **PDF Processing**: `pdfminer.six`
      37
      38 ## 📋 Yêu cầu hệ thống
      39
      40 - Python 3.9+
      41 - Google AI API Key (để sử dụng Gemini)
      42 - Qdrant Cluster URL & API Key
      43
      44 ## ⚙️ Cài đặt
      45
      46 1. **Clone repository**:
      47    ```bash
      48    git clone <repository-url>
      49    cd <repository-folder>/web
      50    ```
      51
      52 2. **Cài đặt môi trường ảo (Khuyến nghị)**:
      53    ```bash
      54    python -m venv .venv
      55    source .venv/bin/activate  # On Windows: .venv\Scripts\activate
      56    ```
      57
      58 3. **Cài đặt thư viện**:
      59    ```bash
      60    pip install -r requirements.txt
      61    # Lưu ý: Cần cài thêm các thư viện sau nếu chưa có trong requirements.txt
      62    pip install google-generativeai qdrant-client pdfminer.six flask-session
      63    ```
      64
      65 4. **Cấu hình API Key**:
      66    Mở file `app.py` và cập nhật các thông tin sau:
      67    - `API_KEY`: Google AI API Key của bạn.
      68    - `QDRANT_URL` & `QDRANT_API_KEY`: Thông tin kết nối Qdrant của bạn.
      69
      70 ## 🚀 Chạy ứng dụng
      71
      72 ```bash
      73 python app.py
      74 ```
      75 Sau đó truy cập vào địa chỉ `http://127.0.0.1:5000` trên trình duyệt.
      76
      77 ## 📝 Hướng dẫn sử dụng
      78
      79 1. Tải lên tệp CV của bạn (định dạng .pdf).
      80 2. Hệ thống sẽ tự động phân tích và tìm kiếm các công việc phù hợp.
      81 3. Bạn có thể xem danh sách công việc và điểm số tương quan.
      82 4. Đặt câu hỏi vào ô chat để nhận tư vấn chi tiết từ chuyên gia ảo (AI).
      83
      84 ---
      85 *Dự án được phát triển nhằm mục đích tối ưu hóa quy trình tuyển dụng và giúp ứng viên tìm thấy công việc
         phù hợp nhất.*