🚀 Đề tài tốt nghiệp
Hệ thống phát hiện giao dịch bất thường kết hợp lưu vết xác thực trên IPFS với kiến trúc dữ liệu đa mô hình

🎯 Mục tiêu
Phát hiện giao dịch bất thường/gian lận bằng mô hình AI không giám sát:

Isolation Forest → anomaly score + nhãn

AutoEncoder → reconstruction error + nhãn + latent embedding

Lưu vết kết quả (hash log) lên IPFS

Cung cấp Dashboard real-time để:

Quản trị, tra cứu, xác minh kết quả

Cảnh báo khi phát hiện bất thường

🧩 Chức năng chính
Anomaly Detection

Tính anomaly score & nhãn (bình thường / bất thường)

IPFS Logging

Tạo hash log (ID, timestamp, label) → lưu lên Pinata → nhận CID

Real-time Alerts & Logs

Redis Pub/Sub → WebSocket → Frontend

User & Permission Management

Auth, RBAC

💡 Công nghệ
Frontend: Next.js, TailwindCSS, Shadcn/UI

Backend: NestJS (REST/gRPC), WebSocket, Kafka

AI/ML: Isolation Forest (scikit-learn), AutoEncoder (PyTorch)

Decentralized Storage: IPFS (Pinata)

Databases: MongoDB (raw data), Redis (cache/alert)

DevOps & Infra: Docker, Nginx, GitHub Actions, Cloudflare, AWS

🔄 Luồng dữ liệu tổng quát
Ingress

Frontend / Socket Gateway nhận giao dịch (REST/WebSocket)

Validation & Lưu raw

NestJS Validate → MongoDB

AI Service

Preprocessing → Isolation Forest → AutoEncoder → lấy anomaly score, reconstruction error, latent embedding

Lưu trữ & Cảnh báo

Raw data → MongoDB

Embedding → VectorDB (Qdrant) – nếu cần truy vấn tương đồng

Hash log → IPFS → nhận CID

Nếu anomaly → Redis Pub/Sub → WebSocket → Frontend

Dashboard

Hiển thị giao dịch, score/error, CID, tìm tương đồng

Auth & RBAC
