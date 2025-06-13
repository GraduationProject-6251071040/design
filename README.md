# 🚀 Đề tài tốt nghiệp

## 🧠 Xây dựng hệ thống phát hiện giao dịch bất thường bằng trí tuệ nhân tạo kết hợp lưu vết xác thực bằng Blockchain với kiến trúc dữ liệu đa mô hình

![Alt text](./image.png)

## 🎯 Mục tiêu đề tài

- Phát hiện các giao dịch bất thường/gian lận dựa trên mô hình AI học không giám sát (_unsupervised learning_).
- Lưu vết kết quả phân tích một cách **minh bạch, không thể sửa đổi** bằng cách lưu **hash log** lên **Blockchain Ethereum (testnet)**.
- Cung cấp **giao diện trực quan** để người dùng quản trị, tra cứu, xác minh kết quả và tìm kiếm hành vi tương đồng bằng **truy vấn vector**.

## 🧩 Các chức năng chính của hệ thống

- ✅ Phát hiện giao dịch bất thường
- ✅ Sinh vector embedding và truy vấn tương đồng
- ✅ Lưu vết kết quả AI bằng Blockchain
- ✅ Quản lý dữ liệu và log phân tích
- ✅ Giao diện web theo dõi cảnh báo và xác minh blockchain
- ✅ Tra cứu hành vi tương tự
- ✅ Hệ thống cảnh báo real-time
- ✅ Quản lý người dùng, phân quyền

## 💡 Các công nghệ chính trong dự án

- **Programming**: JavaScript, TypeScript, Python, Solidity
- **Frontend**: Next.js, TailwindCSS, Shadcn/UI
- **Backend**: NestJS (REST, GraphQL, WebSocket, gRPC)
- **AI/ML**: scikit-learn, PyTorch, AutoEncoder, Isolation Forest
- **Blockchain**: Solidity Smart Contract, Hardhat, Sepolia Testnet, ethers.js
- **Databases**: MongoDB, PostgreSQL, Qdrant (VectorDB), ElasticSearch, Valkey (Redis-compatible)
- **DevOps**: Docker (Kubernetes), Nginx, GitHub Actions, Cloudflare

## 🔄 Luồng dữ liệu tổng thể (Data Flow)

### 1. 🟢 Giao dịch người dùng gửi lên (Entry Point)

- Giao dịch được gửi từ frontend hoặc hệ thống bên ngoài đến **API Gateway** qua:
  - `GraphQL` (NestJS xử lý)

### 2. ⚙️ Xử lý giao dịch tại Backend (NestJS)

- Nhận request → validate → lưu vào `MongoDB` (log tạm thời - raw data)
- Chuyển giao dịch sang **AI Service** để phân tích bất thường

### 3. 🧠 AI Service phân tích bất thường

- AI model (Isolation Forest / AutoEncoder) xử lý và trả về:
  - `Anomaly score`
  - `Label` (bất thường / bình thường)
  - `Vector embedding`

### 4. 💾 Lưu trữ dữ liệu và kết quả AI

| Dữ liệu            | Lưu trữ tại       | Mục đích                              |
| ------------------ | ----------------- | ------------------------------------- |
| Giao dịch gốc      | MongoDB           | Lưu raw transaction                   |
| Thống kê/phân tích | PostgreSQL        | Dashboard, báo cáo                    |
| Vector embedding   | Qdrant (VectorDB) | Tìm kiếm hành vi tương đồng           |
| Log hệ thống       | ElasticSearch     | Truy vấn log, hiển thị theo thời gian |
| Cache / realtime   | Redis (Valkey)    | Tạm lưu & gửi cảnh báo realtime       |

### 5. 🔐 Lưu vết kết quả lên Blockchain

- Backend tạo `hash` từ kết quả AI (ID + timestamp + label)
- Gửi lên **Smart Contract trên Sepolia testnet**
- Trả về `transaction hash` để xác minh kết quả trên blockchain

### 6. 🚨 Gửi cảnh báo nếu phát hiện bất thường

- Nếu phát hiện bất thường:
  - Gửi sự kiện qua `Redis Pub/Sub`
  - Frontend (WebSocket) nhận cảnh báo realtime
  - Ghi log cảnh báo vào ElasticSearch

### 7. 📊 Người dùng xem dashboard (Next.js)

- Người dùng truy cập frontend để:
  - Xem danh sách giao dịch
  - Xem chi tiết kết quả phân tích
  - Tra cứu giao dịch tương đồng (truy vấn Qdrant)
  - Xác minh kết quả AI bằng `ethers.js` trên blockchain

// các fildes để train data
{
"tx_id": "TX0001",
"amount": 1250.00,
"timestamp": "2025-06-05T22:20:00Z",
"type": "withdraw"
}
admin-datn
N7pRQSA3rjbJCcia

mongodb+srv://admin-datn:N7pRQSA3rjbJCcia@cluster0.ocwhkn6.mongodb.net/
