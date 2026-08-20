# Cài AHA Paint trên Windows

> **⬜ BẢN NHÁP — chưa có bản phát hành nào.** Hướng dẫn này viết trước để review; chưa có installer
> để tải. Xem [../README.md](../README.md).

---

## Cần có trước

- Windows 10 hoặc 11 (64-bit)
- Adobe Photoshop **2023 trở lên** (phiên bản 24.0+)
- Google Chrome, đã đăng nhập vào nhà cung cấp AI bạn định dùng (Google Flow / ChatGPT / Reve /
  RunningHub) — AHA Paint dùng **chính phiên đăng nhập của bạn**, không dùng tài khoản của chúng tôi
- Kết nối internet

## Các bước

1. **Tải** `AHA-Studio-Setup-x.y.z.exe` từ trang Releases.
2. **Chạy** file vừa tải. Windows sẽ hiện cảnh báo — xem mục "Cảnh báo của Windows" bên dưới; đây là
   chuyện bình thường, không phải dấu hiệu file có vấn đề.
3. Bấm **Next** vài lần. Không cần quyền Administrator.
4. Cuối quá trình cài, trình duyệt sẽ mở trang cài extension → bấm **Add to Chrome**.
5. Panel Photoshop được cài kèm — xem [../plugin/README.md](../plugin/README.md).
6. **Mở Photoshop** → menu `Plugins` → `AHA Paint`. Đèn kết nối ở đầu panel chuyển **xanh** là xong.
7. Đăng nhập ở tab **Account** trong panel.

## Cảnh báo của Windows khi cài lần đầu

Bạn sẽ thấy một hộp thoại kiểu "Windows protected your PC" hoặc "Unknown publisher".

**Vì sao:** Windows tin những phần mềm đã mua chứng thư ký số từ một nhà cung cấp mà Microsoft công
nhận. Chúng tôi chưa mua (chi phí hàng trăm đô mỗi năm), nên Windows chưa nhận diện được AHA Paint.
Điều này **không** nói gì về nội dung file.

Nói thẳng để bạn không phải đoán: **chúng tôi không ký số bản Windows.** Loại chữ ký làm miễn phí
được (self-signed) chỉ có tác dụng bỏ chữ "Unknown Publisher" trong hộp thoại xin quyền
Administrator — mà AHA Paint cài **per-user, không xin quyền Administrator**, nên nó không xuất hiện
ở bất kỳ đâu bạn nhìn thấy. Thay vào đó chúng tôi làm ba việc **có** tác dụng thật: không nén UPX
(thứ hay bị antivirus nghi ngờ), gửi bản build cho Microsoft Defender trước mỗi lần phát hành quan
trọng, và tự kiểm tỉ lệ báo nhầm trước khi phát hành thay vì đợi bạn báo.

**Cách qua:** bấm **More info** → **Run anyway**.

**Chỉ phải làm một lần.** Các bản cập nhật sau tải bằng chính AHA Paint, không qua trình duyệt, nên
sẽ không hỏi lại. (Đây là điều **thiết kế dựa vào và cần được đo trước khi phát hành** — nếu thực tế
khác, hướng dẫn này phải sửa.)

**Nếu antivirus báo động:** Windows Defender và các antivirus khác đôi khi báo nhầm với phần mềm
Python đã đóng gói, vì cách nó tự giải nén giống hành vi của một số malware. Nếu gặp, hãy báo cho
chúng tôi — chúng tôi sẽ gửi file cho Microsoft để gỡ nhầm lẫn.

## Cài vào đâu

| | Đường dẫn | Có bị ghi đè khi cập nhật? |
|---|---|---|
| Chương trình | `%LOCALAPPDATA%\Programs\AHA Paint\` | Có |
| Cài đặt & khoá của bạn | `%APPDATA%\AHA Paint\` | **Không bao giờ** |

Thư mục thứ hai chứa API key bạn tự nhập và **danh tính máy** của bản cài này. Cập nhật không bao
giờ chạm vào nó. Nếu bạn tự tay xoá thư mục đó, máy này sẽ phải ghép cặp lại với tài khoản của bạn.

## Gỡ cài đặt

`Settings` → `Apps` → `AHA Paint` → `Uninstall`. Cài đặt của bạn được **giữ lại** theo mặc định; muốn
xoá sạch thì tick thêm ô tương ứng trong trình gỡ cài.

## Không chạy được?

| Triệu chứng | Cách xử lý |
|---|---|
| Đèn kết nối trong panel **không xanh** | AHA Paint chưa chạy. Mở nó từ Start Menu, rồi đợi vài giây |
| Panel báo không kết nối được | Có phần mềm khác đang chiếm cổng `8799`. Khởi động lại máy; nếu vẫn vậy, liên hệ hỗ trợ |
| Panel không xuất hiện trong Photoshop | Xem [../plugin/README.md](../plugin/README.md) |
| Nút tạo ảnh báo chưa đăng nhập nhà cung cấp | Mở tab Chrome tới nhà cung cấp đó và đăng nhập, rồi thử lại |
| Nút Shape / Nearly / Exactly chậm ở lần đầu | Lần đầu cần tải gói xử lý ảnh; có thanh tiến độ. Lần sau nhanh ngay |
