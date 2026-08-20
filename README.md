# AHA Studio

Bộ công cụ AI cho người sáng tạo. Ảnh được tạo **trên máy bạn**, bằng phiên đăng nhập của **chính
bạn** với nhà cung cấp AI — không byte pixel nào đi qua máy chủ của chúng tôi.

## ⬇️ Tải về

**[→ Trang tải mới nhất](../../releases/latest)**

| Nền tảng | File | Trạng thái |
|---|---|---|
| **Windows** 10/11 (64-bit) | `AHA-Studio-Setup-x.y.z.exe` | ✅ có sẵn |
| **macOS** | — | ⬜ chưa phát hành |

> File `.exe` nằm ở tab **Releases**, không nằm trong danh sách file của trang này. Đó là cố ý:
> git giữ lại mọi phiên bản của mọi file vĩnh viễn, nên gói cài đặt được phát hành riêng thay vì
> lưu trong repo.

Windows sẽ hiện cảnh báo **"Unknown Publisher"** khi bạn chạy file. Đây là chuyện bình thường với
phần mềm chưa mua chữ ký số — bấm **More info → Run anyway**. Chúng tôi nói thẳng điều này thay vì
giấu đi: [hướng dẫn chi tiết](Windows/README.md).

## Cài gì vào máy

Một file cài đặt duy nhất đặt vào máy bạn:

- **AHA Studio** — chương trình chạy nền, là nơi chứa và quản lý mọi ảnh AI bạn tạo ra, đồng thời
  là cầu nối tới các phần mềm thiết kế.
- **AHA Paint** — panel trong **Photoshop**. Cài kèm sẵn, có thể bỏ chọn khi cài.

Sau này sẽ có thêm **AHA Video** cho Premiere — khi đó nó là một lựa chọn nữa trong cùng file cài
đặt này, không phải một file cài đặt riêng.

## Hướng dẫn

| Bạn cần | Đọc |
|---|---|
| Cài trên Windows, và cách vượt cảnh báo | [Windows/README.md](Windows/README.md) |
| Cài trên macOS ⬜ | [MacOS/README.md](MacOS/README.md) |
| Panel Photoshop — cài, và vì sao nó không tự cập nhật | [plugin/README.md](plugin/README.md) |
| Extension trình duyệt — vì sao cần, và nó làm gì | [chrome_extension/README.md](chrome_extension/README.md) |

## Vài điều nên biết trước khi cài

**Lần đầu bấm nút Shape / Nearly / Exactly**, ứng dụng sẽ tải thêm khoảng **260 MB** thư viện AI,
kèm thanh tiến độ. Bạn không phải tự tải hay tự cài gì — nhưng nếu đang dùng mạng tính theo dung
lượng thì nên biết trước. Các tính năng khác không cần khoản tải này.

**Ảnh của bạn nằm ở máy bạn.** Mặc định là `%APPDATA%\AHA Paint\AHA_studio_data`. Đổi được trong
AHA Studio → Cài đặt → **Nơi lưu** — hữu ích khi ổ C: đầy. Khi đổi, ảnh được **chép sang chỗ mới
rồi mới xoá ở chỗ cũ**, nên gián đoạn giữa chừng cũng không mất gì.

**Chúng tôi không giữ mật khẩu nhà cung cấp AI của bạn.** Ứng dụng dùng phiên đăng nhập sẵn có
trong trình duyệt bạn đang dùng.

## Repo này chứa gì

Chỉ tài liệu hướng dẫn và các bản phát hành. **Không có mã nguồn** — mã nguồn nằm ở một repo riêng,
không công khai.
