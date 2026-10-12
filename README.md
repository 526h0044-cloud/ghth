# GigMe - Siêu Nền Tảng Kết Nối Việc Làm Siêu Nhỏ & Smart Escrow

GigMe là ứng dụng kết nối việc làm siêu nhỏ & dịch vụ tức thì dành cho sinh viên và giới trẻ với cơ chế bảo vệ ký quỹ **Smart Escrow** chống quỵt tiền, định vị Geofence quét radar thời gian thực, và trợ lý AI hỗ trợ công việc.

## 📋 Mục Lục
1. [Tổng Quan Dự Án](#1-tổng-quan-dự-án)
2. [Công Nghệ & Hạ Tầng Kỹ Thuật](#2-công-nghệ--hạ-tầng-kỹ-thuật)
3. [Các Tính Năng Cốt Lõi](#3-các-tính-năng-cốt-lõi)
4. [Chợ Sinh Viên & Trao Đổi Đồ Cũ](#4-chợ-sinh-viên--trao-đổi-đồ-cũ)
5. [Quy Định Tài Chính & Hạn Mức Nạp/Rút](#5-quy-định-tài-chính--hạn-mức-nạp-rút)
6. [Hướng Dẫn Cài Đặt & Chạy Dự Án](#6-hướng-dẫn-cài-đặt--chạy-dự-án)
7. [Bản Đồ Cấu Trúc Mã Nguồn](#7-bản-đồ-cấu-trúc-mã-nguồn)

---

## 1. Tổng Quan Dự Án
GigMe kết nối nhu cầu việc làm bán thời gian, dịch vụ campus và chợ sinh viên. Hệ thống cam kết an toàn tài chính nhờ cơ chế khóa cọc ký quỹ Escrow và thuật toán chống giả mạo tọa độ GPS (`Anti-Fake GPS`).

---

## 2. Công Nghệ & Hạ Tầng Kỹ Thuật
* **Frontend**: React 18, TypeScript, Tailwind CSS v4, Lucide React, Leaflet Maps.
* **Backend & API**: Node.js, Express, Google GenAI SDK (`@google/genai`).
* **Cơ sở dữ liệu**: Cloud Firestore (Firebase) kết hợp LocalStorage/IndexedDB (Offline-First).
* **Đàm thoại VoIP**: WebRTC P2P (DTLS-SRTP) mã hóa trực tiếp hai chiều.

---

## 3. Các Tính Năng Cốt Lõi

1. **Smart Escrow Vault (Bảo Vệ Ký Quỹ An Toàn)**
   - Khóa tiền thù lao của người thuê vào quỹ ký quỹ an toàn khi tạo công việc.
   - Freelancer nộp bài nghiệm thu kèm minh chứng Watermark tọa độ GPS & thời gian thực.
   - Giải ngân tự động sau khi người thuê duyệt nghiệm thu (trừ phí sàn và thuế theo quy định).

2. **Khám Phá Việc Làm Bằng Radar Geofence Tương Tác**
   - Bản đồ radar Leaflet quét công việc lân cận trong khuôn viên trường đại học.
   - Gợi ý công việc thông minh với độ tương thích cao.
   - Bộ lọc chi tiết theo mức thù lao, thời lượng, kèo nhóm (MultiWorker) và kèo định kỳ.

3. **Đấu Giá Ngược (Reverse Auction) & Đăng Kèo 3 Bước Siêu Tốc**
   - Người làm tự đề xuất mức giá và thời gian hoàn thành cạnh tranh.
   - Trợ lý AI Vision hỗ trợ đọc nhận diện thẻ sinh viên và thông tin đơn việc.

4. **Hệ Thống Gọi Thoại & Video WebRTC P2P (VoIP & Video Call)**
   - Đàm thoại âm thanh và video trực tiếp thời gian thực ngay trong ứng dụng, hỗ trợ thu nhỏ nổi (Floating Mini Bubble) để thoải mái chuyển tab.
   - Tính năng lật camera trước/sau linh hoạt, đo vạch sóng tín hiệu động và hiển thị đồng hồ đếm giờ thời gian thực.
   - Tự động lưu lịch sử cuộc gọi (Call Log) kèm nút gọi lại 1-chạm vào khung chat.

5. **Định Danh Nhiều Cấp Độ (KYC Multi-Tier & SSO Sinh Viên)**
   - **Xác thực CCCD chip**: Kiểm tra cấu trúc số chuẩn C06 kết hợp quét sinh trắc học.
   - **Xác thực Email Đại học**: Nhận huy hiệu sinh viên chính quy qua mã OTP `.edu.vn`.

6. **Bảo Mật & Quản Trị Hệ Thống**
   - Cơ chế cô lập luồng chat 1-1 và bộ lọc chống lách sàn (Anti-Leakage) bảo vệ giao dịch.
   - Bảng điều khiển Master Admin phân xử tranh chấp và kiểm toán dòng tiền.

---

## 4. Chợ Sinh Viên & Trao Đổi Đồ Cũ
* **Đăng bán nhanh chóng**: Sinh viên có thể dễ dàng đăng bán hoặc nhượng lại giáo trình cũ, đồ dùng học tập, xe đạp, thiết bị điện tử hay đồ đạc ký túc xá với vài thao tác.
* **Lọc theo trường đại học**: Tìm kiếm các món đồ thanh lý ngay trong nội bộ trường hoặc các trường lân cận trong cùng khu vực campus.
* **Giao dịch an toàn**: Tận dụng hệ thống ví tiền và bảo chứng uy tín của nền tảng giúp hạn chế rủi ro khi mua bán đồ cũ giữa các bạn sinh viên.

---

## 5. Quy Định Tài Chính & Hạn Mức Nạp/Rút
* **Nạp tiền**: Tối đa `10.000.000 VNĐ`/lần, tối đa `30.000.000 VNĐ`/ngày.
* **Rút tiền**: Tối thiểu `50.000 VNĐ`, tối đa `3.000.000 VNĐ`/lần.
* **An toàn tài chính (AML)**: Tiền mới nạp phải cách tối thiểu `60 phút` mới được phép rút ra. Tài khoản yêu cầu tạo ít nhất `5 ngày`, thời gian online tích lũy `3 giờ` và hoàn thành ít nhất `1 công việc`.
* **Trần số dư**: Tài khoản cá nhân không vượt quá `200.000.000 VNĐ`.

---

## 6. Hướng Dẫn Cài Đặt & Chạy Dự Án

```bash
# Cài đặt thư viện
npm install

# Khởi chạy dev server (Port 3000)
npm run dev

# Kiểm tra lỗi cú pháp TypeScript
npm run lint

# Build sản phẩm sản xuất
npm run build

# Khởi chạy server production
npm start
