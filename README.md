# AHA Paint — vùng dàn trang phát hành

> ## ⬜ CHƯA CÓ BẢN PHÁT HÀNH NÀO
>
> Thư mục này chứa **tài liệu hướng dẫn cho người dùng cuối** và **manifest mẫu** — nội dung sẽ được
> đưa lên repo phát hành công khai. Hôm nay chưa có installer, chưa có binary, chưa có bản `.ccx` nào
> được ký. Toàn bộ hướng dẫn ở đây là **bản nháp**, viết trước để lúc phát hành không phải viết gấp,
> và để mọi hứa hẹn với người dùng được review trước khi thành thật.
>
> Trạng thái thật: [docs/product/05_status_and_roadmap.md](../docs/product/05_status_and_roadmap.md) §4.28.

---

## 1. Thư mục này là gì

Đây **không** phải một bản phát hành. Nó là nơi soạn nội dung cho repo công khai
`aha-studio-releases`, nơi người dùng sẽ tải file về:

```
aha-paint            (private)  → source code, workflow build, VERSION
aha-studio-releases   (public)   → GitHub Releases: binary + manifest đã ký + hướng dẫn
```

Tách hai repo vì tải file từ Releases của một repo private cần Personal Access Token, mà nhúng token
vào ứng dụng phân phối là tự tạo một bí mật không thể giữ được.

## 2. Nội dung

| Đường dẫn | Nội dung | Dành cho |
|---|---|---|
| [Windows/README.md](Windows/README.md) | Hướng dẫn cài trên Windows + cách vượt cảnh báo SmartScreen | Người dùng cuối |
| [MacOS/README.md](MacOS/README.md) | Hướng dẫn cài trên macOS + cách vượt cảnh báo Gatekeeper | Người dùng cuối |
| [plugin/README.md](plugin/README.md) | Cài panel Photoshop (`.ccx`) và vì sao nó **không** tự cập nhật | Người dùng cuối |
| [chrome_extension/README.md](chrome_extension/README.md) | Cài extension và vì sao AHA Paint cần nó | Người dùng cuối |
| [version.json.example](version.json.example) | Manifest cập nhật **mẫu** — cấu trúc, không phải bản thật | Người phát hành |

## 3. Quy tắc của thư mục này

1. **Không commit binary vào repo source.** `.gitignore` trong thư mục này chặn `*.zip`, `*.exe`,
   `*.dmg`, `*.pkg`, `*.msi`, `*.ccx`. Binary chỉ tồn tại dưới dạng **GitHub Release asset**, không
   phải file trong git — repo source sẽ phình ra vĩnh viễn và không xoá lại được.
2. **Một cái bẫy đã biết:** `.gitignore` ở gốc repo có dòng `*.ccx`. Nghĩa là một file `.ccx` bỏ vào
   `plugin/` sẽ bị git bỏ qua **âm thầm** — không báo lỗi, chỉ đơn giản không được commit. Đừng dựa
   vào việc thấy file trong thư mục để kết luận nó đã được lưu.
3. **Không đặt bí mật ở đây.** Mật khẩu certificate, private key ký manifest, token phát hành đều
   thuộc GitHub Secrets. Thư mục này là nơi **công khai** theo thiết kế.
4. **Mọi câu hứa với người dùng phải khớp thực tế.** Nếu chưa mua chữ ký số thì hướng dẫn phải nói
   thẳng là sẽ có cảnh báo — che nó đi chỉ làm người dùng nghĩ mình tải phải virus.

## 4. Tài liệu liên quan

| Muốn biết | Đọc |
|---|---|
| Đóng gói thế nào, ký số ra sao, kênh phân phối nào | [docs/product/08_packaging_and_distribution.md](../docs/product/08_packaging_and_distribution.md) |
| Cập nhật hoạt động thế nào, thất bại thì sao | [docs/product/09_auto_update.md](../docs/product/09_auto_update.md) |
| Vì sao chọn từng phương án, phương án nào bị loại | [plan/2026-08-13_packaging_and_auto_update.md](../plan/2026-08-13_packaging_and_auto_update.md) |
| Còn thiếu gì trước khi phát hành được | [docs/product/05_status_and_roadmap.md](../docs/product/05_status_and_roadmap.md) §4.28 |
