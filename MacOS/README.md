# Cài AHA Paint trên macOS

> **⬜ BẢN NHÁP — chưa có bản phát hành nào.** Hướng dẫn này viết trước để review; chưa có gói cài
> để tải. Xem [../README.md](../README.md).
>
> **⚠️ macOS ở bản đầu là BETA.** Bản macOS được build tự động trên máy chủ CI, nhưng **chưa ai chạy
> thử luồng cài này trên một máy Mac thật** — chúng tôi không có sẵn máy Mac để kiểm. Các bước dưới
> đây viết theo đúng tài liệu của Apple, không phải theo quan sát. Nếu bạn gặp khác với mô tả, đó là
> thông tin quý giá — báo cho chúng tôi.

---

## Cần có trước

- macOS 12 (Monterey) trở lên
- Adobe Photoshop **2023 trở lên** (phiên bản 24.0+)
- Google Chrome, đã đăng nhập vào nhà cung cấp AI bạn định dùng (Google Flow / ChatGPT / Reve /
  RunningHub) — AHA Paint dùng **chính phiên đăng nhập của bạn**
- Kết nối internet

## Chọn đúng bản cho máy bạn

Có **hai** bản macOS, không thể dùng lẫn — tải nhầm thì máy báo không mở được.

|  → **About This Mac**, dòng "Chip"/"Processor" | Tải bản |
|---|---|
| **Apple M1 / M2 / M3 / M4…** | `AHA-Paint-macos-arm64-x.y.z.zip` |
| **Intel Core i5 / i7 / i9 / Xeon** | `AHA-Paint-macos-x86_64-x.y.z.zip` |

## Các bước

1. **Tải** đúng file `.zip` theo bảng trên từ trang Releases.
2. **Giải nén** (double-click).
3. **Double-click `install.command`.** macOS sẽ hiện cảnh báo — xem mục dưới.
4. Cửa sổ Terminal mở ra, báo "Đã cài xong", rồi bạn đóng nó.
5. Panel Photoshop cài riêng — xem [../plugin/README.md](../plugin/README.md).
6. Cài extension cho Chrome — xem [../chrome_extension/README.md](../chrome_extension/README.md).
7. **Mở Photoshop** → menu `Plugins` → `AHA Paint`. Đèn kết nối chuyển **xanh** là xong.
8. Đăng nhập ở tab **Account** trong panel.

## Cảnh báo của macOS khi mở lần đầu

Bạn sẽ thấy đại ý *"không thể mở vì Apple không thể kiểm tra xem nó có chứa mã độc hay không"*.

**Vì sao:** macOS chỉ tin phần mềm có Developer ID **do chính Apple cấp** — không có nhà cung cấp
nào khác thay thế được, và không có mức phí thấp hơn $99/năm. Chúng tôi chưa đăng ký. Điều này
**không** nói gì về nội dung file.

**Cách qua — macOS 15 (Sequoia) trở lên:**

1. Double-click `install.command` một lần. macOS sẽ chặn — đó là điều được chờ đợi, cứ đóng hộp thoại.
2. Mở **System Settings** → **Privacy & Security**.
3. Kéo xuống mục **Security** — sẽ có một dòng nhắc tới AHA Paint vừa bị chặn.
4. Bấm **Open Anyway**, xác thực bằng Touch ID hoặc mật khẩu máy.

> **Chuột phải → Open không còn dùng được từ macOS 15.** Apple thông báo nguyên văn: *"In macOS
> Sequoia, users will no longer be able to Control-click to override Gatekeeper when opening software
> that isn't signed correctly or notarized. They'll need to visit System Settings > Privacy & Security
> to review security information for software before allowing it to run."* Hướng dẫn nào bảo bấm
> chuột phải → Open là hướng dẫn viết cho macOS cũ.

**macOS 14 trở xuống:** chuột phải (hoặc Control-click) → **Open** → **Open** lần nữa vẫn dùng được.

Script `install.command` sẽ tự bỏ dấu "tải từ Internet" khỏi bản đã cài, nên **bạn chỉ phải làm điều
này một lần** — với chính file vừa tải. Nếu sau này bạn tải **một file `.zip` mới** qua trình duyệt
thì sẽ bị hỏi lại; còn các bản cập nhật do chính AHA Paint tải thì không. (Thiết kế dựa vào điều này
và nó **cần được đo trước khi phát hành**.)

## Cài vào đâu

| | Đường dẫn | Có bị ghi đè khi cập nhật? |
|---|---|---|
| Chương trình | `~/Applications/AHA Paint.app` | Có — thay **cả** bundle, không vá từng file |
| Cài đặt & khoá của bạn | `~/.config/aha-paint` | **Không bao giờ** |

Thư mục thứ hai chứa API key bạn tự nhập và **danh tính máy** của bản cài này. Nếu bạn tự tay xoá,
máy này sẽ phải ghép cặp lại với tài khoản của bạn.

## Tự chạy khi mở máy (không bắt buộc)

Nếu muốn AHA Paint sẵn sàng ngay khi bạn mở Photoshop, cài thêm LaunchAgent — bản phát hành sẽ kèm
hướng dẫn. Không cài cũng không sao: mở AHA Paint thủ công rồi mới mở panel là đủ.

## Gỡ cài đặt

Xoá `~/Applications/AHA Paint.app`. Cài đặt của bạn ở `~/.config/aha-paint` **vẫn còn** — xoá thư mục
đó nếu muốn sạch hoàn toàn (sau đó máy này sẽ phải ghép cặp lại).

## Không chạy được?

| Triệu chứng | Cách xử lý |
|---|---|
| Đèn kết nối trong panel **không xanh** | AHA Paint chưa chạy. Mở nó từ Applications rồi đợi vài giây |
| `install.command` không mở được | Làm theo mục cảnh báo ở trên: **System Settings → Privacy & Security → Open Anyway** (macOS 15+). Chuột phải → Open chỉ còn dùng được trên macOS 14 trở xuống |
| Tải về, giải nén xong mà máy báo không mở được ứng dụng | Có thể bạn tải nhầm bản. Kiểm  → About This Mac rồi đối chiếu bảng "Chọn đúng bản cho máy bạn" ở đầu trang |
| Panel không xuất hiện trong Photoshop | Xem [../plugin/README.md](../plugin/README.md) |
| Nút tạo ảnh báo chưa đăng nhập nhà cung cấp | Mở tab Chrome tới nhà cung cấp đó và đăng nhập, rồi thử lại |
| Nút Shape / Nearly / Exactly chậm ở lần đầu | Lần đầu cần tải gói xử lý ảnh; có thanh tiến độ |
