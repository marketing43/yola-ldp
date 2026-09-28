# Template ZNS — Kết quả test phong cách học

Đăng ký trên Zalo OA Admin → ZNS → Tạo template. Loại template: **Tùy chỉnh** (custom), tag **Tag 2 (Chăm sóc khách hàng)** vì gửi ngay sau khi khách chủ động làm test. Tránh Tag 3 vì giới hạn 4 tin/user/tháng.

Quy tắc đã biết từ Freetest (giữ nguyên): mỗi user chỉ nhận 1 tin cùng template/ngày; khung giờ 6h00–19h59; tham số ≤ 30 ký tự với text ngắn.

## Template 1 — Gửi kết quả (chính)

**Tên template:** Kết quả test phong cách học - DISC
**Logo:** logo YOLA (file gốc)
**Tiêu đề:** Kết quả phong cách học của bé <child_name>

**Nội dung:**
```
Chào <parent_name>,

Bé <child_name> thuộc nhóm <disc_type_name>: <disc_tagline>

YOLA gửi ba mẹ 4 gợi ý để đồng hành với con:
```

**Bảng thông tin (table):**
| Nhãn | Tham số |
|---|---|
| Cách học hợp với con | `<tip_learn>` |
| Ba mẹ nên tránh | `<tip_avoid>` |
| Ở nhà cùng con | `<tip_home>` |
| Lớp phù hợp | `<program>` |

**Nút:** `Xem kết quả đầy đủ` → URL `https://uudai.yola.vn/phong-cach-hoc-cua-con/?r=<result_code>` (loại nút: mở link)
**Nút 2 (tùy chọn):** `Nhắn YOLA tư vấn` → mở chat OA

**Tham số + độ dài + giá trị mẫu (để Zalo duyệt):**
| Tham số | Kiểu | Max | Mẫu |
|---|---|---|---|
| parent_name | text | 30 | Chị Lan |
| child_name | text | 24 | Bơ |
| disc_type_name | text | 30 | Ngôi Sao Kết Nối |
| disc_tagline | text | 60 | Vui vẻ, thích trò chuyện và toả sáng khi có người cùng chơi. |
| tip_learn | text | 90 | Học qua đóng vai, bài hát, kể chuyện và trò chơi nhóm. |
| tip_avoid | text | 90 | Phê bình con trước mặt người khác. |
| tip_home | text | 90 | Quay video con kể chuyện bằng tiếng Anh gửi ông bà. |
| program | text | 30 | Tiếng Anh Thiếu nhi (6–11 tuổi) |
| result_code | text | 20 | I7D2S2C1 |

Lưu ý khi đăng ký: Zalo hay từ chối tham số text dài > 60 ký tự ở phần body. Nếu bị từ chối, chuyển 3 dòng tip vào bảng (table cho phép dài hơn) hoặc rút mỗi tip còn ≤ 60 ký tự. Bảng giá trị theo 4 nhóm để mapping nằm trong `index.html` (đối tượng `TYPES`, lấy phần tử đầu của `learn`/`avoid`/`home`).

Tham số `result_code` chưa dùng đến trên web. Nếu muốn nút "Xem kết quả đầy đủ" mở đúng trang kết quả không cần làm lại test, cần dev thêm: web đọc `?r=` và render thẳng kết quả. Hiện tại nút chỉ mở LDP.

## Template 2 — Nhắc sau 3 ngày (nurturing, tùy chọn)

Chỉ dùng cho lead intent = "warm" hoặc "result_only". Tag 2.

**Tiêu đề:** Ba mẹ đã thử cách học cho bé <child_name> chưa?

**Nội dung:**
```
Chào <parent_name>,

3 ngày trước, bé <child_name> có kết quả nhóm <disc_type_name>. Ba mẹ đã thử gợi ý "<tip_home>" ở nhà chưa?

Nếu muốn giáo viên YOLA xếp lớp đúng phong cách học của con, ba mẹ đặt lịch kiểm tra trình độ miễn phí tại trung tâm gần nhà.
```
**Nút:** `Đặt lịch kiểm tra miễn phí` → mở chat OA (hoặc link LDP thi thử/freetest tùy chương trình đang chạy)

## Việc dev cần làm để bắn ZNS
1. Webhook nhận lead (LEAD_WEBHOOK_URL trong `index.html`, hiện để trống) → ghi Sheet.
2. Apps Script đọc dòng mới → map `disc_type` → 4 tham số tip → gọi ZNS API với template 1. Tái dùng hàm gửi ZNS của Freetest (Code.gs), thêm property `ZNS_DISC_TEMPLATE`.
3. Ghi `zns_status` vào Sheet như Freetest.
4. Template 2 chạy bằng trigger theo giờ, quét dòng đủ 3 ngày và intent phù hợp.

## Trường dữ liệu web đang gửi về webhook (JSON)
`source, submitted_at, page_url, parent_name, phone, area, intent (hot/warm/other_center/result_only), child_name, child_age, respondent (parent/child), disc_type (D/I/S/C), disc_type_name, disc_secondary, score_d, score_i, score_s, score_c, answers (chuỗi 12 ký tự), recommended_program, utm{...}, referrer, repeat_child (true khi PH làm cho bé thứ 2 với cùng SĐT)`
