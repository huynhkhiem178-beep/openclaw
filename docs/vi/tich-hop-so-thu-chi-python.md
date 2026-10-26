# Tích hợp OpenClaw với Sổ Thu Chi Python

Tài liệu này phác thảo cách kết nối OpenClaw với dự án [Sổ Thu Chi Python](https://github.com/huynhkhiem178-beep/du-an-thu-chi-python) mà không trộn hai bộ mã nguồn thành một khối khó bảo trì.

## 1. Tình trạng hiện tại

Sổ Thu Chi Python hiện là ứng dụng desktop Tkinter và chương trình terminal, dùng các file JSON để lưu giao dịch và ngân sách. OpenClaw là một dự án riêng, có Gateway, công cụ, skills và plugins.

**Chưa có tích hợp chạy được ở thời điểm viết tài liệu này.** Chỉ thêm đường dẫn đến repository không khiến OpenClaw tự động đọc hay sửa dữ liệu thu chi.

## 2. Kiến trúc đề xuất

```text
Tin nhắn tiếng Việt
        │
        ▼
OpenClaw
        │ gọi công cụ với dữ liệu có cấu trúc
        ▼
Cầu nối Python chạy cục bộ
        │ xác thực và kiểm tra quyền
        ▼
Lớp nghiệp vụ Sổ Thu Chi
        │
        ▼
transactions.json / monthly_budgets.json
```

Nên giữ ứng dụng thu chi thành repository riêng, rồi xây dựng một cầu nối nhỏ có giao diện lập trình ổn định. Không nên để mô hình AI tự do sửa file JSON trực tiếp.

## 3. Các chức năng nên triển khai theo thứ tự

1. **Chỉ đọc:** xem tổng thu, tổng chi, số dư và báo cáo theo tháng.
2. **Thêm giao dịch:** nhận loại giao dịch, số tiền, danh mục, ngày và ghi chú; kiểm tra dữ liệu trước khi lưu.
3. **Ngân sách:** đọc hạn mức và số đã chi trong tháng.
4. **Sửa hoặc xóa:** chỉ làm sau khi có xác nhận rõ ràng của người dùng.
5. **Kiểm thử:** kiểm tra số tiền không hợp lệ, ngày sai định dạng, tháng không có giao dịch, file dữ liệu lỗi và yêu cầu không đầy đủ.

## 4. Ví dụ hội thoại mong muốn

- “Tổng kết thu chi tháng này.”
- “Tháng này tui đã chi bao nhiêu cho ăn uống?”
- “Tạo khoản chi 25.000 đồng, danh mục ăn uống, ghi chú ăn sáng hôm nay.”

Trước khi ghi giao dịch, trợ lý nên tóm tắt nội dung và yêu cầu xác nhận, ví dụ: “Tạo khoản chi 25.000 đồng — danh mục Ăn uống — ghi chú Ăn sáng. Bạn xác nhận chứ?”

## 5. Nguyên tắc an toàn

- Cầu nối chỉ lắng nghe trên máy cục bộ theo mặc định; không mở cổng ra Internet.
- Dùng danh sách thao tác cho phép, không thực thi lệnh shell tùy ý từ tin nhắn.
- Xác thực số tiền dương, ngày hợp lệ, loại thu/chi và danh mục.
- Yêu cầu xác nhận trước khi ghi, sửa hoặc xóa giao dịch.
- Sao lưu dữ liệu trước khi thay đổi định dạng hoặc cấu trúc lưu trữ.
- Không commit file giao dịch hay ngân sách cá nhân lên GitHub.
- Tạo test tự động cho các thao tác đọc và ghi trước khi kết nối với OpenClaw.

## 6. Lộ trình thực hiện

- [ ] Rà soát cách ứng dụng hiện tại đọc và ghi JSON.
- [ ] Tách các thao tác thu chi thành những hàm nghiệp vụ có thể gọi mà không cần mở giao diện Tkinter.
- [ ] Viết cầu nối Python với các thao tác được giới hạn rõ ràng.
- [ ] Viết test cho cầu nối.
- [ ] Đăng ký cầu nối thành công cụ/skill theo cơ chế được phiên bản OpenClaw đang dùng hỗ trợ.
- [ ] Thử nghiệm cục bộ trước, bắt đầu bằng quyền chỉ đọc.
- [ ] Chỉ bật ghi dữ liệu sau khi cơ chế xác nhận và kiểm thử đã hoàn tất.

**Kết luận:** Có thể kết hợp hai dự án. Cách bền vững nhất là giữ ứng dụng thu chi riêng và kết nối qua một lớp Python nhỏ, có kiểm soát quyền, thay vì chép toàn bộ mã nguồn thu chi vào bên trong OpenClaw.
