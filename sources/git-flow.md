# Git Flow

Sử dụng Git giúp quản lý các phiên bản nâng cấp của web ổn định và có thể khôi phục, xem các thay đổi trước khi phát hành.

## Nguyên tắc chính

### Commit

**Commit phải sử dụng tiếng Anh**

Cấu trúc

```
TicketID Verb + something + where
```

Ví dụ:

```
CDD-12 Fix text alignment in Hero homepage
TTD-35 Update text color in About page
```

Lưu ý:

- Commit có ticket ID ở đầu, vd **CD-12 Fix bug in hero homepage** (nếu có, để track việc đã giao ở đâu).
- Không chia động từ, để nguyên dạng, ví dụ **Fix, Update, Setup, Remove, Add**
- Dùng tính từ bổ ngữ danh từ, ví dụ `text color` (chủ thể là **color**) khác `color text` (chủ thể là **text**)

**Commit Files**

- Commit không chứa các file compiled (vd `.min.css`, `.min.js`) do công cụ tạo ra. Trừ trường hợp commit update cả plugin hoặc theme gốc.

### Nhánh chính phụ và quy tắc đặt tên

Các nhánh chính, chỉ cho code vào sau khi đã approve và duyệt QA

- **master**: nhánh chính, chứa code trên môi trường **live**
- **develop**: nhánh chính, chứa code trên môi trường **dev**

Các nhánh phụ, làm các nhiệm vụ và thường checkout gốc theo quy ước để làm ra.

**Checkout từ `develop`**

- **feature/<feature-name>**: làm tính năng hoặc page template mới
- **bugfix/<dev-name>/<mm-dd-yyyy>**: nếu tính năng đã được cho lên nhánh `develop`, dev làm tiếp bugfix.

**Checkout từ `master`**

- **hotfix/<mm-dd-yyyy>**: nếu trên live có lỗi cần fix gấp
