# Panel AHA Paint cho Photoshop

> Panel đi **kèm trong file cài đặt**, không tải riêng. Nó **không được ký số** — giống chính file
> cài đặt, nên Creative Cloud sẽ hỏi xác nhận khi cài. Xem [../README.md](../README.md).

---

## Đây là gì

Phần bạn **nhìn thấy và bấm** khi dùng AHA Paint: một panel nằm trong Photoshop. Nó được phát hành
dưới dạng một file `.ccx` — định dạng plugin của Adobe.

Panel **không** tự tạo ảnh. Nó nói chuyện với AHA Paint (chương trình chạy trên máy bạn), và chương
trình đó dùng phiên đăng nhập trình duyệt của **chính bạn** để làm việc với nhà cung cấp AI. Ảnh
không đi qua máy chủ của chúng tôi.

## Yêu cầu

Adobe Photoshop **2023 trở lên** (phiên bản 24.0+). Photoshop cũ hơn sẽ không nạp được panel.

## Cài

Installer đã cài panel giúp bạn. Nếu cần cài tay:

1. Double-click file `AHA-Paint-x.y.z.ccx`.
2. Adobe Creative Cloud nhận file và cài vào Photoshop.
3. **Khởi động lại Photoshop.**
4. Menu `Plugins` → `AHA Paint`.

Cần có ứng dụng **Creative Cloud Desktop** trên máy để bước 2 hoạt động.

## Panel không xuất hiện?

| Kiểm tra | Cách làm |
|---|---|
| Photoshop có đủ mới? | `Help` → `About Photoshop`, cần 24.0 trở lên |
| Đã khởi động lại Photoshop? | Đóng **hẳn** Photoshop rồi mở lại — nạp plugin chỉ xảy ra lúc khởi động |
| Creative Cloud có nhận plugin? | Mở app Creative Cloud → `Stock & Marketplace` → `Plugins` → `Manage plugins` |
| Vẫn không thấy | Cài lại `.ccx` rồi khởi động lại Photoshop; nếu vẫn vậy, liên hệ hỗ trợ |

## Panel **không** tự cập nhật — đây là giới hạn của Adobe

Chương trình AHA Paint trên máy bạn tự cập nhật được. **Panel thì không.** Adobe không cho một plugin
tự ghi đè chính nó khi đang chạy, nên nút "Cập nhật" trong panel chỉ có thể mở link tải — bạn phải
cài lại `.ccx` như lần đầu.

Vì vậy panel được thiết kế để **ít cần cập nhật**: nó gọi một giao diện cố định, ít thay đổi.

Khi nào bạn thật sự **cần** cập nhật panel: khi panel hiện thông báo rằng nó quá cũ so với chương
trình đang chạy trên máy. Lúc đó chỉ tính năng liên quan bị tạm khoá, kèm link tải — **không** phải
cả panel ngừng dùng được.

## Đèn kết nối ở đầu panel

| Màu | Nghĩa |
|---|---|
| **Xanh** | Panel đang nói chuyện được với AHA Paint. Sẵn sàng |
| **Đỏ / xám** | Không thấy AHA Paint. Mở chương trình đó lên (Start Menu / Applications) rồi đợi vài giây |

Đèn xanh nghĩa là *kết nối* ổn. Nó **không** nói rằng bạn đã đăng nhập nhà cung cấp AI, cũng không
nói bạn còn hạn dùng — hai thứ đó panel báo riêng, bằng chữ.
