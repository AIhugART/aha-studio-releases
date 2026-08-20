# aha-studio-releases

Đây là repo **công khai** duy nhất của hệ sinh thái AHA Studio. Nó tồn tại vì một lý do kỹ thuật
duy nhất: tải file từ GitHub Releases của một repo private cần Personal Access Token, và nhúng
token vào ứng dụng phân phối cho người dùng là tự tạo một bí mật không thể giữ được.

**Repo này KHÔNG chứa source code.** Source nằm ở repo private `aha-paint`.

---

## 0. Đọc trước khi làm bất cứ điều gì

Repo này là thứ **người dùng cuối tải về**. Mọi file ở đây đều là thứ ai đó sẽ chạy trên máy họ,
hoặc là lời hứa họ sẽ tin. Ba hệ quả:

1. **Không bịa số liệu.** Dung lượng, thời gian tải, yêu cầu hệ thống — nếu không đo được thì viết
   "chưa đo", đừng ước lượng. Một con số sai ở đây là một người dùng chuẩn bị sai.
2. **Không hứa thứ chưa tồn tại.** Nếu một tính năng chưa phát hành, nói thẳng là chưa. Repo này
   từng có nguyên một khối cảnh báo "⬜ CHƯA CÓ BẢN PHÁT HÀNH NÀO" ở đầu README chính vì lý do đó.
3. **Không tự ý upload binary.** Xem §3 — binary phải đến từ một quy trình build cụ thể trong repo
   private, không phải từ máy của bất kỳ ai.

---

## 1. Tên gọi — dùng sai là mô tả sai sản phẩm

| Tên | Là gì | Đích |
|---|---|---|
| **AHA Studio** | **Toàn bộ hệ sinh thái**, và cũng là app trung tâm chạy cục bộ (quản lý ảnh, đăng nhập, điều phối) | — |
| **AHA Paint** | **Chỉ** là plugin cho Photoshop | Photoshop |
| **AHA Video** | **Chỉ** là plugin cho Premiere — ⬜ chưa phát hành | Premiere |

Sai lầm hay gặp nhất và hậu quả của nó:

- ❌ "AHA Paint là bộ công cụ AI của bạn" → sai, AHA Paint là **một** plugin trong bộ đó.
- ❌ "Cài AHA Paint để dùng AHA Studio" → ngược. Installer cài **AHA Studio** (daemon dùng chung);
  AHA Paint là một **component tuỳ chọn** bên trong nó.
- ❌ "AHA Studio trong Photoshop" → sai sản phẩm. Trong Photoshop là **AHA Paint**.

Installer tên `AHA-Studio-Setup-x.y.z.exe` **không phải** lỗi đánh máy: nó cài daemon — hạ tầng
dùng chung cho cả hệ sinh thái — rồi mới cài plugin Photoshop như một thành phần con.

---

## 2. Cấu trúc repo

```
README.md                 Trang đầu người dùng thấy
Windows/README.md         Hướng dẫn cài trên Windows
MacOS/README.md           Hướng dẫn cài trên macOS  (⬜ chưa từng chạy thật)
plugin/                   Hướng dẫn cài panel Photoshop (.ccx)
chrome_extension/         Hướng dẫn cài extension    (⬜ kênh phân phối chưa quyết)
version.json.example      MẪU cấu trúc manifest tự cập nhật — KHÔNG phải manifest thật
```

**GitHub Releases** giữ file thật (binary + manifest đã ký). Git tree giữ **văn bản**. Đừng commit
binary vào git tree — đó là lý do Releases tồn tại.

---

## 3. Ai được upload, và upload cái gì

Mọi artifact phải đến từ script build trong repo private `aha-paint`:

| Asset | Sinh bởi | Ghi chú |
|---|---|---|
| `AHA-Studio-Setup-x.y.z.exe` | `scripts/packaging/build_installer.py` | Bọc sẵn daemon + plugin Photoshop |
| `aha-tier2_<abi>_vx.y.z.zip` | `scripts/packaging/build_tier2_pack.py` | ~260 MB. App **tự tải** khi user bấm nút detector lần đầu — người dùng không tải tay |
| `version.json` + `version.json.sig` | `scripts/packaging/sign_manifest.py` | Chữ ký Ed25519 **rời**, ký trên đúng byte thô |

**Không bao giờ tự dựng artifact ở đây.** Repo này không có source để dựng, và một binary không
truy được về commit nào là một binary không ai kiểm chứng được.

### Thứ tự bắt buộc khi thêm gói tầng 2

1. Upload `.zip` lên Release **trước**.
2. **Rồi mới** dán `sha256`/`size_bytes`/URL vào `daemon/preprocessors/tier2_pack.py` ở repo private.
3. Build lại daemon — hash nằm **bên trong** binary.

Đảo thứ tự (dán hash trước, upload bản build khác sau) ⇒ mọi người dùng verify fail **sau khi đã
tải xong 260 MB**.

---

## 4. `version.json` — file duy nhất có thể làm hỏng máy người dùng từ xa

Đây là manifest tự cập nhật: daemon trên máy user đọc nó để biết có bản mới không và tải ở đâu.

**Bất biến, không thương lượng:**

- Chữ ký nằm ở **file riêng** `version.json.sig`, không phải một field bên trong JSON. Lý do: chữ ký
  tính trên **byte thô**; nhúng field vào rồi phải loại nó ra và dựng lại canonical JSON để verify —
  chỉ cần `json.dumps()` của bên ký và bên verify khác nhau một chút (đặc biệt `ensure_ascii` với
  chữ có dấu trong changelog) là **mọi bản phát hành hỏng chữ ký cùng lúc**.
- `sha256` trong mỗi platform object **chỉ** chống lỗi đường truyền. Nó nằm cùng file với URL nên
  một mình nó không chống được kẻ tấn công — `version.json.sig` mới là thứ chống giả mạo.
- **Không sửa `version.json` bằng tay trên Release.** Sửa một ký tự là chữ ký chết, và daemon sẽ
  từ chối bản cập nhật — đúng như thiết kế.
- Tên key theo platform (`windows_x86_64`, `macos_arm64`, …) là **hợp đồng**. Thêm key mới thì được;
  **đổi tên** một key sau khi client đã phát hành là phá hợp đồng với đúng những bản cài cũ không
  thể tự sửa.

Đặc tả từng field: `docs/product/09_auto_update.md` §3 trong repo private.

---

## 5. Viết tài liệu cho người dùng ở đây thế nào

- **Tiếng Việt là ngôn ngữ chính.** Người dùng của sản phẩm này là người Việt.
- **Nói thẳng chỗ xấu.** Windows sẽ hiện cảnh báo "Unknown Publisher" vì chưa mua chữ ký số —
  viết rõ điều đó và cách bấm qua. Giấu đi thì người dùng tưởng máy nhiễm virus và bỏ cài.
- **Đánh dấu trạng thái tường minh:** ✅ đã chạy thật · 🧪 có code + test nhưng chưa chạy thật ·
  ⬜ chưa làm. Đừng để người đọc đoán.
- **Đừng chép trạng thái từ repo private sang đây.** Nó sẽ lệch. Nói cái gì đang tải được **hôm
  nay**, đó là thứ duy nhất trang này cần đúng.

---

## 6. Việc KHÔNG được làm trong repo này

| Không | Vì sao |
|---|---|
| Commit binary vào git tree | Repo public + file lớn = clone chậm vĩnh viễn; Releases sinh ra cho việc này |
| Commit khoá riêng, PAT, hay bất kỳ credential nào | Public repo — lộ là lộ vĩnh viễn, kể cả sau khi xoá commit |
| Sửa tay `version.json` đã publish | Chết chữ ký, chặn cập nhật của mọi user |
| Xoá một asset Release đã phát hành | Daemon trên máy user đang trỏ URL đó; xoá = bản cập nhật hỏng giữa chừng |
| Viết hướng dẫn cho tính năng chưa phát hành | Người dùng sẽ đi tìm thứ không tồn tại |
| Đổi `AppId` của installer | Windows coi là app khác ⇒ user có 2 entry trong Add/Remove Programs và phải gỡ tay |

---

## 7. Khi không chắc

Repo này chỉ **phân phối**. Mọi câu hỏi "nó hoạt động thế nào / vì sao thiết kế vậy" đều thuộc repo
private `aha-paint`:

- Quy trình đóng gói từng bước → `docs/product/08_packaging_and_distribution.md` §9
- Cơ chế tự cập nhật → `docs/product/09_auto_update.md`
- Trạng thái thật của từng tính năng → `docs/product/05_status_and_roadmap.md`

Không đoán. Nếu câu trả lời không nằm trong repo này, nó nằm ở đó.
