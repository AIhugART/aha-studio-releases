# Extension Chrome của AHA Paint

> **⬜ BẢN NHÁP.** Chưa có bản extension nào được phát hành, **và kênh phân phối còn chưa chốt** —
> xem mục "Cách cài" bên dưới. Xem thêm [../README.md](../README.md).

---

## Vì sao AHA Paint cần một extension

AHA Paint không có tài khoản AI riêng để tạo ảnh cho bạn. Nó dùng **tài khoản của chính bạn** ở nhà
cung cấp bạn chọn — Google Flow, ChatGPT, Reve, hay RunningHub — thông qua phiên đăng nhập đã có
trong Chrome của bạn.

Extension chính là cầu nối đó: nó nhận yêu cầu từ AHA Paint trên máy bạn, thao tác trên trang của
nhà cung cấp giống như bạn tự làm, rồi trả ảnh về Photoshop.

Hệ quả của thiết kế này, nói thẳng cả hai chiều:

- ✅ **Không** ai phải giao mật khẩu hay API key của nhà cung cấp cho chúng tôi. Chúng tôi không lưu,
  không nhìn thấy, không truyền đi credential nào của bạn.
- ✅ Ảnh của bạn **không** đi qua máy chủ của chúng tôi.
- ⚠️ Vì việc tạo ảnh chạy trên tài khoản của bạn, mọi hạn mức, chi phí và điều khoản sử dụng của nhà
  cung cấp áp dụng cho **tài khoản của bạn**. Với RunningHub, vượt hạn mức miễn phí sẽ tiêu điểm
  trong ví của bạn.

Nếu bạn không muốn dùng cách này, AHA Paint có các nhà cung cấp gọi **API trực tiếp** (bạn tự dán API
key của mình trong tab Settings) — không cần extension, không cần Chrome.

## Cách cài

**⬜ Chưa quyết định** giữa hai đường, và việc chưa quyết là có chủ đích:

| Đường | Ưu | Nhược |
|---|---|---|
| **Chrome Web Store** (kể cả chế độ Unlisted) | Cài một cú bấm; Chrome tự cập nhật ngầm | Phải qua xét duyệt; chưa xác minh chính sách với extension thao tác trang bên thứ ba |
| **Nạp thủ công** (Developer mode) | Không phụ thuộc xét duyệt | Nhiều bước; Chrome nhắc nhở định kỳ; không tự cập nhật |

Đường nào được chọn phụ thuộc kết quả kiểm tra chính sách của Chrome Web Store — việc này chưa làm,
và bản hướng dẫn chính thức sẽ chỉ viết sau khi có câu trả lời rõ ràng. Trạng thái:
[docs/product/05_status_and_roadmap.md](../../docs/product/05_status_and_roadmap.md) §4.28, giả định
**A4**.

## Cập nhật

Nếu phát hành qua Chrome Web Store: Chrome **tự** cập nhật ngầm, bạn không phải làm gì. Không có cách
nào để AHA Paint buộc Chrome cập nhật ngay — nếu extension của bạn quá cũ, panel sẽ hiện thông báo
kèm phiên bản tối thiểu cần có.

## Extension này cần quyền gì

Chỉ quyền thao tác trên trang của các nhà cung cấp AI mà AHA Paint hỗ trợ, cộng quyền nói chuyện với
chương trình AHA Paint trên chính máy bạn (`127.0.0.1`). Bản phát hành sẽ liệt kê danh sách chính xác
kèm lý do từng quyền.

## Không chạy được?

| Triệu chứng | Cách xử lý |
|---|---|
| Popup extension báo **Disconnected** | Chương trình AHA Paint chưa chạy. Mở nó rồi đợi vài giây |
| Panel báo "không có worker nào kết nối" | Extension chưa được cài hoặc đang bị tắt. Kiểm trong `chrome://extensions` |
| Panel báo bạn chưa đăng nhập nhà cung cấp | Mở một tab tới trang nhà cung cấp đó và đăng nhập, rồi thử lại |
| Đóng tab nhà cung cấp giữa lúc đang tạo ảnh | Lượt đó sẽ báo lỗi rõ ràng thay vì treo. Mở lại tab và thử lại |
