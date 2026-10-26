# OpenClaw 🦞 — Trợ lý của bạn, trên thiết bị và ứng dụng trò chuyện của bạn

OpenClaw là một trợ lý AI mã nguồn mở chạy trên máy tính của chính bạn và có thể kết nối với những nền tảng nhắn tin bạn đang sử dụng, chẳng hạn như Discord, iMessage, Slack, Teams, Telegram, WhatsApp cùng hơn 20 nền tảng khác. Dự án cũng có ứng dụng cho macOS, iOS, Android, Windows và Linux.

Một **Gateway** có thể vận hành OpenClaw như trợ lý cá nhân trên máy tính xách tay hoặc như một hệ thống dùng chung cho cả nhóm. Khác biệt chủ yếu nằm ở cấu hình.

## Quyền riêng tư và quyền kiểm soát

Dữ liệu trạng thái, bộ nhớ và thông tin xác thực được lưu trên phần cứng của bạn. Bạn có thể thay đổi nhà cung cấp mô hình AI và bộ công cụ tác tử (ví dụ Claude, Codex hoặc mô hình chạy cục bộ) thông qua plugin.

Nội dung bạn gửi sẽ được chuyển đến nhà cung cấp mô hình và nền tảng trò chuyện mà bạn cấu hình, cùng với dữ liệu chẩn đoán nếu bạn chủ động bật xuất dữ liệu. Theo tài liệu dự án, mặc định OpenClaw chỉ tự kiểm tra phiên bản mỗi ngày; việc gửi thống kê tính năng ẩn danh là tùy chọn. Có thể tắt các kiểm tra này bằng cấu hình `update.checkOnStart: false`.

OpenClaw được quản lý bởi OpenClaw Foundation, một tổ chức độc lập phi lợi nhuận. Dự án không có gói trả phí, dịch vụ lưu trữ do dự án cung cấp hay token riêng.

- [Trang chủ OpenClaw](https://openclaw.ai)
- [Tài liệu chính thức](https://docs.openclaw.ai)
- [Bắt đầu sử dụng](https://docs.openclaw.ai/start/getting-started)
- [Vì sao chọn OpenClaw?](https://docs.openclaw.ai/start/why-openclaw)
- [Câu hỏi thường gặp](https://docs.openclaw.ai/help/faq)

## 1. Cài đặt

Trình cài đặt hỗ trợ macOS, Linux và Windows. Khi cần, trình cài đặt sẽ thiết lập môi trường Node.js tương thích.

### macOS / Linux / WSL2

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

### Windows PowerShell

```powershell
iwr -useb https://openclaw.ai/install.ps1 | iex
```

Nếu bạn đã tự quản lý Node.js, có thể cài gói OpenClaw bằng npm. Yêu cầu phiên bản Node.js: 24.16 trở lên hoặc 26.1 trở lên; dự án khuyến nghị Node.js 26.

```bash
npm install -g openclaw@latest --allow-scripts=openclaw
```

Lệnh trên dành cho npm 12 hoặc npm 11.16 trở lên. Với npm 11.15 trở xuống, hãy bỏ tùy chọn `--allow-scripts=openclaw`. Xem [hướng dẫn cài đặt](https://docs.openclaw.ai/install) để biết thêm về Docker, Nix và các cách triển khai khác.

## 2. Bắt đầu nhanh

Sau khi cài đặt mới, trình cài đặt thường tự khởi chạy quy trình thiết lập. Hãy hoàn tất các bước mà nó hiển thị.

Nếu bạn cài trực tiếp bằng npm, pnpm hoặc Bun, hãy chạy:

```bash
openclaw onboard --install-daemon
```

Sau khi thiết lập xong, kiểm tra Gateway và mở giao diện điều khiển:

```bash
openclaw gateway status
openclaw dashboard
```

Quy trình thiết lập sẽ kiểm tra quyền truy cập mô hình AI, tạo thư mục làm việc và cấu hình Gateway. Lệnh cuối mở giao diện Control UI; hãy gửi thử một tin nhắn để xác nhận trợ lý hoạt động.

Xem [hướng dẫn bắt đầu](https://docs.openclaw.ai/start/getting-started) để thiết lập các kênh trò chuyện và xử lý sự cố.

## 3. Các thành phần hoạt động cùng nhau

- **Gateway:** trung tâm điều khiển cục bộ, quản lý phiên làm việc, công cụ, sự kiện và kết nối các kênh.
- **Control UI, CLI và TUI:** các giao diện để kết nối và điều khiển Gateway.
- **Channels (kênh):** kết nối trợ lý với WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, iMessage và các dịch vụ nhắn tin khác.
- **Ứng dụng đồng hành và node:** bổ sung tính năng giọng nói, Canvas, máy ảnh, màn hình và thao tác trên thiết bị ở những nền tảng được hỗ trợ.

OpenClaw có thể dùng mô hình AI trên dịch vụ đám mây hoặc mô hình chạy cục bộ. Bạn có thể mở rộng chức năng bằng công cụ (tools), kỹ năng (skills) và plugin.

- [Nhà cung cấp mô hình AI](https://docs.openclaw.ai/concepts/model-providers)
- [Công cụ](https://docs.openclaw.ai/tools)
- [Kỹ năng](https://docs.openclaw.ai/tools/skills)
- [Plugin](https://docs.openclaw.ai/plugins)

## 4. Bảo mật

Hãy coi tin nhắn đến là dữ liệu không đáng tin cậy. Theo mặc định, các kênh hỗ trợ tin nhắn riêng sẽ yêu cầu ghép nối người gửi chưa biết. Để chấp thuận một yêu cầu ghép nối, dùng lệnh:

```bash
openclaw pairing approve <channel> <code>
```

Trong phiên làm việc chính, công cụ chạy trên máy chủ của bạn trừ khi bạn cấu hình môi trường cách ly (sandbox). Trước khi cho người khác sử dụng hoặc mở Gateway ra mạng bên ngoài, hãy đọc:

- [Hướng dẫn bảo mật](https://docs.openclaw.ai/gateway/security)
- [Hướng dẫn xử lý việc để lộ dịch vụ](https://docs.openclaw.ai/gateway/security/exposure-runbook)
- [Hướng dẫn sandbox](https://docs.openclaw.ai/gateway/sandboxing)

## 5. Tìm tài liệu theo mục đích

| Bạn muốn làm gì? | Tài liệu nên đọc |
| --- | --- |
| Cấu hình mô hình và xác thực | [Mô hình](https://docs.openclaw.ai/concepts/models) · [Nhà cung cấp mô hình](https://docs.openclaw.ai/concepts/model-providers) |
| Kết nối ứng dụng nhắn tin | [Các kênh](https://docs.openclaw.ai/channels) |
| Thêm công cụ, kỹ năng và plugin | [Công cụ](https://docs.openclaw.ai/tools) · [Kỹ năng](https://docs.openclaw.ai/tools/skills) · [Plugin](https://docs.openclaw.ai/plugins) · [ClawHub](https://clawhub.ai) |
| Chạy ứng dụng và kết nối thiết bị | [Nền tảng](https://docs.openclaw.ai/platforms) · [Nodes](https://docs.openclaw.ai/nodes) |
| Dùng dòng lệnh và lệnh trò chuyện | [Tài liệu CLI](https://docs.openclaw.ai/cli) · [Lệnh gạch chéo](https://docs.openclaw.ai/tools/slash-commands) |
| Cấu hình hoặc vận hành Gateway | [Cấu hình](https://docs.openclaw.ai/gateway/configuration) · [Kiến trúc](https://docs.openclaw.ai/concepts/architecture) · [Cập nhật](https://docs.openclaw.ai/install/updating) · [Các kênh phát hành](https://docs.openclaw.ai/install/development-channels) |

## 6. Phát triển mã nguồn

Kho mã nguồn sử dụng **pnpm workspace**. Không hỗ trợ chạy `npm install` ở thư mục gốc của kho mã nguồn.

Các lệnh cơ bản để lấy mã và xây dựng dự án:

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
pnpm install
pnpm build
pnpm ui:build
```

Xem [CONTRIBUTING.md](CONTRIBUTING.md) để biết quy trình đóng góp mã và [hướng dẫn thiết lập môi trường phát triển](https://docs.openclaw.ai/start/setup).

## 7. Quản trị dự án và cộng đồng

OpenClaw được phát triển công khai dưới sự quản lý của OpenClaw Foundation. Quỹ tuyển dụng nhóm nòng cốt và ký các bản phát hành. Các nhà tài trợ hỗ trợ kinh phí và hạ tầng nhưng không sở hữu hay điều khiển dự án.

- [Quy trình đóng góp](CONTRIBUTING.md)
- [Báo lỗi và đề xuất tính năng](https://github.com/openclaw/openclaw/issues/new/choose)
- [Cộng đồng hỗ trợ chính thức](https://community.openclaw.ai/)
- [Báo cáo lỗ hổng bảo mật](SECURITY.md)
- [Xây dựng plugin](https://docs.openclaw.ai/plugins/building-plugins)
- [ClawHub](https://clawhub.ai)

OpenClaw được tạo ra cho Molty, một trợ lý AI hình tôm hùm không gian, bởi Peter Steinberger và cộng đồng.

## 8. Giấy phép

OpenClaw sử dụng giấy phép [MIT](LICENSE). Xem [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) để biết thông tin về mã nguồn bên thứ ba được tích hợp hoặc điều chỉnh.

---

**Lưu ý:** Đây là bản dịch tiếng Việt dễ đọc của tài liệu giới thiệu và bắt đầu sử dụng. Tên lệnh, đường dẫn, tên cấu hình và mã kỹ thuật được giữ nguyên để bạn có thể làm theo hướng dẫn chính xác. Các tài liệu chuyên sâu khác trong kho sẽ cần được dịch tiếp theo từng nhóm.
