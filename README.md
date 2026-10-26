# OpenClaw 🦞 — Trợ lý AI cá nhân của bạn

<p align="center">
  <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-banner-dark.png" alt="OpenClaw — Trợ lý AI chạy trên thiết bị của bạn" width="100%" />
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=flat-square&label=ki%E1%BB%83m%20th%E1%BB%AD" alt="Trạng thái CI"></a>
  <a href="https://www.npmjs.com/package/openclaw"><img src="https://img.shields.io/npm/v/openclaw?style=flat-square&label=phi%C3%AAn%20b%E1%BA%A3n%20npm" alt="Phiên bản npm"></a>
  <a href="https://nodejs.org"><img src="https://img.shields.io/node/v/openclaw?style=flat-square" alt="Phiên bản Node.js"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/gi%E1%BA%A5y%20ph%C3%A9p-MIT-green?style=flat-square" alt="Giấy phép MIT"></a>
</p>

**OpenClaw** là trợ lý AI mã nguồn mở có thể chạy trên máy tính của bạn và kết nối với các ứng dụng nhắn tin như Discord, Telegram, WhatsApp, Slack cùng nhiều nền tảng khác. Dự án cũng hỗ trợ các nền tảng macOS, iOS, Android, Windows và Linux.

Tài liệu này được viết lại bằng tiếng Việt để người mới dễ đọc hơn. Tên lệnh, tên cấu hình và thuật ngữ kỹ thuật cần thiết vẫn được giữ nguyên để tránh làm sai hướng dẫn.

> **Lưu ý:** Đây là bản fork cá nhân để tìm hiểu và tùy chỉnh OpenClaw. Hãy xem giấy phép và hướng dẫn của dự án gốc trước khi phân phối bản sửa đổi.

## 📌 Mục lục

- [OpenClaw làm được gì?](#-openclaw-làm-được-gì)
- [Cách hoạt động tổng quan](#-cách-hoạt-động-tổng-quan)
- [Cài đặt trên Windows](#-cài-đặt-trên-windows)
- [Bắt đầu sử dụng](#-bắt-đầu-sử-dụng)
- [Kết hợp với dự án Sổ Thu Chi Python](#-kết-hợp-với-dự-án-sổ-thu-chi-python)
- [Bảo mật cần lưu ý](#-bảo-mật-cần-lưu-ý)
- [Tài liệu chính thức](#-tài-liệu-chính-thức)
- [Phát triển mã nguồn](#-phát-triển-mã-nguồn)
- [Giấy phép](#-giấy-phép)

## ✨ OpenClaw làm được gì?

- **Trợ lý AI cá nhân:** trò chuyện với mô hình AI đã cấu hình.
- **Kết nối ứng dụng nhắn tin:** đưa trợ lý đến những kênh mà bạn thường dùng.
- **Công cụ và kỹ năng:** mở rộng khả năng của trợ lý bằng tools, skills và plugins.
- **Chạy trên thiết bị của bạn:** cấu hình nơi lưu trữ dữ liệu và cách chạy phù hợp với nhu cầu.
- **Tùy chỉnh:** có thể nghiên cứu mã nguồn, viết tiện ích và phát triển tính năng mới.

OpenClaw không đồng nghĩa với một mô hình AI duy nhất. Nó là hệ thống kết nối mô hình AI, công cụ, kênh trò chuyện và các thành phần thực thi.

## 🧩 Cách hoạt động tổng quan

| Thành phần | Ý nghĩa dễ hiểu |
|---|---|
| **Gateway** | Trung tâm điều phối phiên trò chuyện, công cụ và kết nối |
| **Control UI** | Giao diện web để điều khiển và trò chuyện với trợ lý |
| **CLI** | Giao diện dòng lệnh để cài đặt và quản lý |
| **Channels** | Kết nối các nền tảng nhắn tin |
| **Skills** | Hướng dẫn trợ lý thực hiện một nhóm nhiệm vụ cụ thể |
| **Plugins** | Thành phần mở rộng có thể bổ sung chức năng |
| **Model provider** | Dịch vụ hoặc mô hình AI mà trợ lý sử dụng |

Tìm hiểu chi tiết trong [tài liệu kiến trúc](https://docs.openclaw.ai/concepts/architecture).

## 💻 Cài đặt trên Windows

Mở **PowerShell** và chạy trình cài đặt chính thức:

```powershell
iwr -useb https://openclaw.ai/install.ps1 | iex
```

Chỉ chạy lệnh cài đặt khi bạn tin tưởng nguồn cung cấp. Nếu muốn kiểm tra nội dung script trước khi chạy, hãy mở trang [cài đặt chính thức](https://docs.openclaw.ai/install) và đọc hướng dẫn hiện hành.

Nếu bạn đã tự cài Node.js và muốn cài gói npm, tham khảo hướng dẫn chính thức để chọn phiên bản Node.js/npm tương thích:

```bash
npm install -g openclaw@latest --allow-scripts=openclaw
```

> Không chạy `npm install` ở thư mục gốc của mã nguồn OpenClaw. Repository này sử dụng **pnpm workspace**.

## 🚀 Bắt đầu sử dụng

Sau khi cài đặt, hoàn tất trình hướng dẫn thiết lập. Nếu cài gói trực tiếp bằng npm, pnpm hoặc Bun, có thể khởi chạy quy trình thiết lập bằng:

```bash
openclaw onboard --install-daemon
```

Kiểm tra Gateway và mở giao diện điều khiển:

```bash
openclaw gateway status
openclaw dashboard
```

Quy trình thiết lập sẽ hướng dẫn cấu hình mô hình AI và tạo workspace. Các tùy chọn có thể thay đổi theo phiên bản, vì vậy hãy đối chiếu với [hướng dẫn bắt đầu chính thức](https://docs.openclaw.ai/start/getting-started).

## 💰 Kết hợp với dự án Sổ Thu Chi Python

Tôi có một dự án Python riêng để ghi chép thu nhập, chi tiêu, số dư, lọc giao dịch theo tháng và đặt ngân sách tháng:

**[Mở dự án Sổ Thu Chi Python](https://github.com/huynhkhiem178-beep/du-an-thu-chi-python)**

Dự án hiện có giao diện desktop bằng Tkinter và phiên bản terminal; dữ liệu được lưu cục bộ bằng JSON. Có thể phát triển hướng tích hợp để người dùng trò chuyện với OpenClaw bằng tiếng Việt, ví dụ:

- “Tháng này tui đã chi bao nhiêu?”
- “Ghi khoản chi 25.000 đồng cho ăn sáng.”
- “Tổng thu và tổng chi tháng này là bao nhiêu?”
- “Tui còn bao nhiêu ngân sách?”

### Cách tích hợp đề xuất

OpenClaw sẽ nhận yêu cầu ngôn ngữ tự nhiên, sau đó gọi một lớp kết nối cục bộ có quyền hạn giới hạn. Lớp này sẽ xác thực dữ liệu và làm việc với dữ liệu của ứng dụng Sổ Thu Chi. Giao diện Tkinter hiện tại vẫn có thể được dùng độc lập.

```text
Người dùng
   │  “Ghi khoản chi 25.000 đồng cho ăn sáng”
   ▼
OpenClaw (hiểu yêu cầu)
   │
   ▼
Công cụ tích hợp cục bộ (kiểm tra dữ liệu)
   │
   ▼
Ứng dụng Sổ Thu Chi Python
   │
   ▼
Dữ liệu JSON trên máy người dùng
```

**Trạng thái hiện tại:** hai dự án vẫn là hai repository riêng. README này mới mô tả hướng tích hợp; chưa có cầu nối hoạt động giữa OpenClaw và ứng dụng thu chi. Để tích hợp thật, cần bổ sung một API hoặc công cụ cục bộ có giao diện rõ ràng, kiểm thử và xác nhận trước khi ghi/sửa/xóa giao dịch.

Xem hướng dẫn thiết kế: [Tích hợp OpenClaw với Sổ Thu Chi Python](docs/vi/tich-hop-so-thu-chi-python.md).

## 🔐 Bảo mật cần lưu ý

- Xem tin nhắn nhận được là dữ liệu chưa đáng tin cậy.
- Không công khai Gateway ra Internet nếu chưa hiểu rõ cơ chế xác thực và bảo mật.
- Không cho phép người lạ ghi, sửa hoặc xóa dữ liệu tài chính.
- Với thao tác ghi/sửa/xóa giao dịch, nên yêu cầu người dùng xác nhận trước khi thực hiện.
- Không đưa file dữ liệu cá nhân như `transactions.json` hoặc `monthly_budgets.json` lên GitHub.
- Đọc [hướng dẫn bảo mật](https://docs.openclaw.ai/gateway/security), [hướng dẫn sandbox](https://docs.openclaw.ai/gateway/sandboxing) và [hướng dẫn về dữ liệu gửi đi](https://docs.openclaw.ai/gateway/telemetry).

## 📚 Tài liệu chính thức

| Bạn muốn tìm hiểu | Tài liệu |
|---|---|
| Bắt đầu sử dụng | [Getting started](https://docs.openclaw.ai/start/getting-started) |
| Cài đặt | [Installation](https://docs.openclaw.ai/install) |
| Gateway | [Gateway](https://docs.openclaw.ai/gateway) |
| Kết nối ứng dụng nhắn tin | [Channels](https://docs.openclaw.ai/channels) |
| Công cụ | [Tools](https://docs.openclaw.ai/tools) |
| Kỹ năng | [Skills](https://docs.openclaw.ai/tools/skills) |
| Plugin | [Plugins](https://docs.openclaw.ai/plugins) |
| Cấu hình | [Configuration](https://docs.openclaw.ai/gateway/configuration) |
| Bảo mật | [Security](https://docs.openclaw.ai/gateway/security) |
| Câu hỏi thường gặp | [FAQ](https://docs.openclaw.ai/help/faq) |

## 🛠️ Phát triển mã nguồn

Để lấy mã nguồn gốc và xây dựng dự án, cần cài Git, Node.js tương thích và pnpm. Các lệnh cơ bản:

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
pnpm install
pnpm build
pnpm ui:build
```

Đây là lệnh khởi đầu theo hướng dẫn dự án; hãy xem [hướng dẫn thiết lập môi trường phát triển](https://docs.openclaw.ai/start/setup) và [quy trình đóng góp](CONTRIBUTING.md) trước khi sửa mã.

## 🤝 Cộng đồng và báo lỗi

- [Trang chủ OpenClaw](https://openclaw.ai)
- [Tài liệu](https://docs.openclaw.ai)
- [Cộng đồng](https://community.openclaw.ai/)
- [Báo lỗi / đề xuất tính năng](https://github.com/openclaw/openclaw/issues/new/choose)
- [Hướng dẫn đóng góp](CONTRIBUTING.md)

## 📄 Giấy phép

OpenClaw sử dụng giấy phép [MIT](LICENSE). Xem [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) để biết thông tin về mã nguồn bên thứ ba được tích hợp hoặc điều chỉnh.

---

<p align="center">
  <strong>Đọc hiểu từng bước · Thử nghiệm cẩn thận · Giữ an toàn cho dữ liệu</strong>
</p>
