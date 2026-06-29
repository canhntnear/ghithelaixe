# 📇 Hệ Thống Quản Lý Thẻ Nhận Dạng Lái Xe - Vạn Phú Khánh
Ứng dụng web (Web App) hỗ trợ đọc và ghi dữ liệu đồng bộ vào **Thẻ lái xe đa năng** phục vụ cho các thiết bị Giám sát hành trình (Định vị bách khoa/BCA). Tích hợp bộ lọc giọng nói thông minh hỗ trợ nhập liệu nhanh bằng micro.
---
## 🚨 LƯU Ý QUAN TRỌNG: THIẾT BỊ & TRÌNH DUYỆT HỖ TRỢ
Tính năng tương tác thẻ NFC qua Web (WebNFC) yêu cầu chính sách bảo mật rất ngặt nghèo từ các nhà phát triển hệ điều hành:
*   **Trình duyệt khuyên dùng:** **`GOOGLE CHROME` trên Android** (Bắt buộc phải bật định vị/NFC trên điện thoại).
*   **Trình duyệt Brave, Firefox, Edge, Opera...:** **KHÔNG CHẠY ĐƯỢC**. Brave chủ động chặn hoàn toàn thư viện WebNFC để bảo vệ quyền riêng tư. Nếu lỡ mở bằng Brave, hãy **Copy đường dẫn và dán vào Google Chrome**.
*   **Thiết bị iPhone (iOS):** **KHÔNG HỖ TRỢ** ứng dụng web này do Apple khóa tính năng WebNFC trên trình duyệt (chỉ app cài từ App Store mới dùng được NFC).
---
## ✨ Các Tính Năng Chính
1.  **🔍 Kiểm tra thiết bị (Check Phone):** Tự động phát hiện điện thoại có chip NFC hay không, trình duyệt đang dùng có bị chặn (như Brave) hay không để đưa ra hướng dẫn xử lý trực quan.
2.  **🎤 Nhập liệu bằng giọng nói (AI Mic AI):**
    *   Tách biệt 2 nút Micro cho Số GPLX và Họ tên để tránh nhận diện nhầm.
    *   Tự động dịch từ khóa số (ví dụ: *"Không chín ba hai"* ➡️ `0932`).
    *   Tự động lọc bỏ các từ thừa như *"Tên lái xe là..."*, *"Họ và tên..."*.
3.  **🔠 Chuẩn hóa dữ liệu tự động:**
    *   Số GPLX: Giới hạn chuẩn xác đúng 12 ký tự số.
    *   Họ tên: Tự động xóa dấu tiếng Việt, chuyển in hoa chuẩn theo định dạng máy in/máy quẹt thẻ (Ví dụ: `Nguyễn Văn A` ➡️ `NGUYEN VAN A`).
4.  **🔒 Thuật toán mã hóa & Checksum:** Tự động tính toán phân rã chuỗi nhị phân (gồm 60 bytes dữ liệu) kèm mã kiểm tra lỗi Checksum ở byte thứ 15 và byte thứ 59, đảm bảo thẻ ghi ra đạt chuẩn 100% của Bộ Công an, không bị lỗi cấu trúc khi cắm vào đầu đọc xe.
---
## 🛠️ Hướng Dẫn Sử Dụng Cho Kỹ Thuật Viên
### 1. Cách Kiểm Tra Điện Thoại
*   Bấm vào nút **`🔍 Check Phone`** ở đầu trang.
*   Nếu hiển thị màu xanh lá: Điện thoại và trình duyệt đã sẵn sàng quẹt thẻ.
*   Nếu hiển thị màu cam/đỏ: Hãy kiểm tra lại xem đã bật NFC trong cài đặt máy chưa, hoặc chuyển sang app **Chrome** nếu đang lỡ dùng **Brave**.
### 2. Quy Trình Ghi Thẻ Mới
*   **Bước 1:** Nhập số GPLX (12 số) và Họ tên (hoặc dùng nút 🎤 để đọc).
*   **Bước 2:** Bấm nút **`GHI VÀO THẺ`**. Lúc này màn hình sẽ báo trạng thái chờ.
*   **Bước 3:** Áp chặt thẻ chip vào **vùng lưng điện thoại** (thường nằm gần cụm camera hoặc chính giữa mặt lưng). Giữ im khoảng 2-3 giây cho đến khi màn hình báo **"Ghi thẻ thành công!"**.
### 3. Quy Trình Kiểm Tra Thẻ (Đọc Thẻ)
*   **Bước 1:** Bấm nút **`KIỂM TRA THẺ`**.
*   **Bước 2:** Đưa thẻ vào sau lưng điện thoại để quét.
*   Hệ thống sẽ giải mã dữ liệu cấu trúc và hiển thị kết quả kiểm tra lên bảng thông tin phía dưới. Nếu thẻ lỗi hoặc sai định dạng byte, hệ thống sẽ cảnh báo ngay lập tức.
--
## 💻 Cấu Trúc Payload Dữ Liệu Trên Thẻ (60 Bytes)

Dành cho lập trình viên muốn đồng bộ hệ thống phần cứng khác:
*   `00` - `14` (15 bytes): Chuỗi ký tự số GPLX (bù khoảng trống `0x20`).
*   `15` (1 byte): Checksum của phân vùng GPLX.
*   `16` - `58` (43 bytes): Chuỗi ký tự Họ và Tên không dấu (bù byte trống `0x00`).
*   `59` (1 byte): Checksum của phân vùng Họ tên.
---
## 📞 Liên Hệ & Hỗ Trợ Kỹ Thuật - Vạn Phú Khánh
*   🛒 **Đặt mua phôi thẻ lái xe đa năng:** [0588.588.114](tel:0588588114)
*   ⚙️ **Hỗ trợ lỗi thiết bị & phần mềm:** [0585.114.114](tel:0585114114)
Viết hoàn toàn bằng AI và có thể mắc sai sót.
