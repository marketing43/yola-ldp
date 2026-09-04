# yola-ldp — Quy tắc bắt buộc cho mọi LP trong repo này

Repo deploy các landing page tại uudai.yola.vn. Đọc file này trước khi dựng/sửa LP.

## Quy tắc đã chốt (26/08/2026 — không hỏi lại)

1. **Nơi lưu file: chỉ lưu trong repo này.** Mỗi LP một thư mục con (vd `tieng-anh-cho-be/`).
   KHÔNG tạo bản sao ở `YOLA-landingpage-cowork/output/` hay bất cứ đâu khác.
2. **Trang cảm ơn: dùng chung** `cam-on-ban-da-de-lai-thong-tin/` ở gốc repo.
   KHÔNG tạo trang cảm ơn riêng cho từng LP. Redirect từ LP con: `../cam-on-ban-da-de-lai-thong-tin/`.
   Trigger GTM `Page URL contains cam-on` vẫn khớp.
3. **Thư mục `YOLA-landingpage-cowork` chỉ phục vụ dự án trang freetest**, không liên quan
   các LP khóa học trong repo này (vẫn tra dữ liệu nguồn courses/brand/blocks ở đó khi cần,
   nhưng không ghi output vào đó).
4. **Assets dùng chung** `assets/` ở gốc repo — LP con trỏ `../assets/`, không nhân bản ảnh/font.
   Hệ quả: file index.html tải rời (vd về Downloads) sẽ không hiện ảnh — phải mở từ đúng
   vị trí trong repo hoặc xem trên domain sau khi push.

## Cấu trúc hiện tại

- `index.html` — LP đa khóa (trang chủ uudai.yola.vn)
- `tieng-anh-cho-be/` — LP Tiếng Anh cho bé 4–14 tuổi (YIP/JP/JS), Google Ads back to school
- `tieng-anh-hoc-thuat-nen-tang/` — LP EFL
- `cam-on-ban-da-de-lai-thong-tin/` — trang cảm ơn dùng chung (mọi form redirect về đây)
- `assets/` — ảnh + font dùng chung

## Typography — không để rớt chữ (chốt 26/08/2026)

Không để 1–2 từ lẻ rơi xuống thành dòng cuối của heading/đoạn. Mọi LP nhúng:
`h1,h2,h3,h4,.sec-title{text-wrap:balance}` và `p,li{text-wrap:pretty}`.
Sau khi dựng, soát screenshot 1440px + 390px; còn rớt chữ thì rút gọn câu hoặc nối 2 từ cuối bằng `&nbsp;`.

## Cấu trúc LP tieng-anh-cho-be (v6 — chốt 28/08/2026, layout hiện hành)

Nguyên tắc đã chốt với user: mỗi section trả lời một câu hỏi của phụ huynh, một hình ảnh chủ đạo để nhớ; không thêm section "làm cho có".
Flow: hero (3 ảnh bé tròn + mascot) → dải trust 4 số → Vì sao chọn YOLA (user giữ tạm, sẽ yêu cầu xóa khi hoàn thiện) → Ưu đãi dạng băng ngang compact (#uu-dai, offer-copy tự chuyển sau 31/08) → **Bản đồ hành trình** (#chuong-trinh: đường sóng SVG 4 trạm ảnh tròn + mascot, trạm = #mam-non/#thieu-nhi/#thieu-nien, click mở popup #cmodal; mobile chuyển rail dọc) → Form giữa → **"Một tuần của con"** (#hoat-dong: 4 khung polaroid Trong lớp → Workshop → App → Tin nhắn ba mẹ, kèm carousel 6 workshop + modal ảnh) → Thành tích/Bằng chứng → Video phụ huynh (ẩn chờ PARENT_VIDEOS) → Trung tâm → FAQ (chứa cam kết #cam-ket) → Form cuối.
Đã gỡ ở v6: biểu đồ bậc thang + timeline (thay bằng bản đồ hành trình), section công nghệ riêng (gộp vào Một tuần của con), video YouTube Yola Learning, section giáo viên (khôi phục từ _backup v5 khi có ảnh + hồ sơ GV thiếu nhi).

## Cấu trúc cũ (v5, tham khảo — backup _backup/tieng-anh-cho-be_2026-08-26_v5.html)

Flow đã chốt với user, không tự đổi:
hero → Vì sao chọn YOLA → Ưu đãi B2S (#uu-dai) → Chương trình & Lộ trình hợp nhất (#chuong-trinh: biểu đồ bậc thang + timeline 3 mốc #mam-non/#thieu-nhi/#thieu-nien + mốc tiếp nối 14+; mỗi mốc có nút và click bậc thang mở popup #cmodal chi tiết khóa) → Form giữa (#dang-ky) → Lợi ích kèm theo (Hoạt động ngoại khóa → Đồng hành sau giờ học) → Thành tích (#thanh-tich) → Video phụ huynh (#phu-huynh) → Giáo viên (#giao-vien) → Trung tâm → FAQ → Form cuối (#dang-ky-2).
Nội dung chi tiết khóa nằm TĨNH trong 3 div .cm-content của #cmodal (tốt cho quality score). Section "mô hình lớp học" cũ đã bỏ — nội dung nằm trong popup từng khóa.

## Cấu trúc cũ (v3-v4, tham khảo)

- Nav 5 mục: Tiếng Anh Bé Mầm non (#mam-non) · Thiếu nhi (#thieu-nhi) · Thiếu niên (#thieu-nien) · Trung tâm (#trung-tam) · Ưu đãi (#uu-dai)
- Ưu đãi: badge ngắn ở hero + section #uu-dai riêng sau phần chương trình; mọi text ưu đãi có class `offer-copy` + `data-evergreen`, tự chuyển sau 31/08/2026 23:59
- Không có section cam kết riêng (chỉ 1/3 khóa có cam kết) — nguyên văn cam kết + đủ điều kiện nằm trong FAQ `<details id="cam-ket">`, link #cam-ket tự mở
- Section giáo viên: đang dùng tạm 9 GV luyện thi — chờ user cấp ảnh + hồ sơ GV thiếu nhi để thay
- Section video phụ huynh (#phu-huynh): tự ẩn khi `PARENT_VIDEOS` rỗng; có video thì điền `{id:'youtube_id', title:'...'}` vào mảng trong index.html

## Nhận diện "trẻ em" cho LP tieng-anh-cho-be (chốt 26/08/2026)

Chất trẻ em đến từ ảnh + màu + mascot, không đổi font (brand chỉ cho SVN-Gilroy).
- Hero: cụm 3 ảnh bé hình tròn kèm chip tuổi (img_kid_yip/jp/js.webp — đã crop bỏ logo góc, nguồn thumbnail PRODUCT IMAGES) + mascot vẫy trên form
- Mascot voi (từ brandguide, đã convert webp trong assets/): img_mascot_wave (hero), img_mascot_gift (ưu đãi), img_mascot_flag (đỉnh biểu đồ lộ trình), img_mascot_read (FAQ)
- Section Ưu đãi nền vàng nhạt, section Hoạt động nền hồng nhạt (màu phụ vẫn ≤20% theo brand)
- Section Hoạt động ngoại khóa đặt ngay sau "Vì sao chọn YOLA", trước Chương trình
- Backup các bản cũ nằm ở _backup/ (tieng-anh-cho-be_2026-08-26_v3.html)

## Truyền thông ưu đãi bằng TIỀN, không dùng % (user chốt 03/09/2026)

Mọi copy ưu đãi trên LP tieng-anh-cho-be chỉ dùng số tiền, luôn kèm "đến", làm tròn XUỐNG:
- Trong đợt B2S 09/2026 (đến 20/09): "tiết kiệm đến 18 triệu" (từ 18.071.200 combo 4 YIP/JP/JS)
- Fallback tự động sau 20/09: "tiết kiệm đến 14 triệu" (base 22% combo 4 = 14.071.200) — KHÔNG ghi 18 triệu ngoài đợt B2S vì mức đó gồm học bổng B2S
- Khi có promotion tháng mới: tính lại số tiền từ bảng gốc rồi thay cả hai mức

## CẢNH BÁO — Unicode và URL ảnh yola.vn (bài học 04/09/2026)

File ảnh học viên trên yola.vn (wp-content) có tên tiếng Việt lưu dạng NFD (dấu tách rời).
KHÔNG BAO GIỜ normalize Unicode (NFC) cho cả file HTML — sẽ đổi byte của URL và làm 404 ảnh.
Nếu cần sửa lỗi font dấu tiếng Việt: chỉ normalize phần TEXT, giữ nguyên mọi chuỗi https://yola.vn/...
(hoặc normalize xong thì đối chiếu lại URL với bản gốc như đã làm ở vụ này).
