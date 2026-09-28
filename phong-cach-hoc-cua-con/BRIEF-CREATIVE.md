# Brief creative — LDP "Con bạn thuộc kiểu học nào?"

Ngày brief: 28/09/2026 · Người brief: Marketing (Tuyền) · Deadline đề xuất: 7 ngày làm việc
Xem bản dựng thử: `yola-ldp/phong-cach-hoc-cua-con/index.html` (mở trong repo, hiện đang dùng icon tạm thay nhân vật).

## 1. Bối cảnh
LDP quiz 12 câu, 5 phút, cho PH có con 4–14 tuổi. Kết quả trả về 1 trong 4 nhóm tính cách (theo mô hình DISC). Trang này KHÔNG phải LP bán khóa: tone vui, nhẹ, giống một trò chơi nhỏ. PH làm xong muốn lưu thẻ kết quả và khoe lên FB/Zalo.

Cần 2 hạng mục: (A) 4 nhân vật đại diện 4 nhóm, (B) thẻ kết quả để share.

## 2. Hạng mục A — 4 nhân vật

| Nhóm | Tên | Màu chủ đạo | Tính cách | Gợi ý tư thế/đạo cụ |
|---|---|---|---|---|
| D | Thủ Lĩnh Nhí | Cam đỏ `#FF6B57` | Quyết đoán, thích thử thách, muốn về nhất | Giơ tay/cờ lên cao, đứng trên bục, băng đô đội trưởng |
| I | Ngôi Sao Kết Nối | Vàng `#F2B705` | Hoạt bát, thích giao lưu, nhiều ý tưởng | Cầm micro/loa, ngôi sao bay xung quanh, đang cười lớn |
| S | Người Bạn Ấm Áp | Xanh lá `#4DBB1B` | Kiên nhẫn, tốt bụng, biết lắng nghe | Ôm gấu bông hoặc đang chia bánh cho bạn, trái tim nhỏ |
| C | Nhà Khám Phá Tỉ Mỉ | Xanh dương `#179EF1` | Cẩn thận, tò mò, ngăn nắp | Kính lúp, sổ tay, đeo kính, đang quan sát |

Yêu cầu bắt buộc:
- Nhân vật là **thiết kế riêng của YOLA**, không dựa trên nhân vật/hình khối của PeopleKeys hay bất kỳ bộ DISC nào khác. Không dùng hình người mặc áo chữ D/I/S/C.
- Cùng một hệ với mascot voi hiện có (`assets/img_mascot_*.webp`): nét dày bo tròn, màu phẳng, mắt to. Có thể là 4 bạn voi nhỏ khác trang phục, hoặc 4 bạn động vật khác nhau nhưng cùng phong cách vẽ. Chốt hướng với Marketing trước khi vẽ full.
- Không phân biệt giới tính rõ ràng (PH của cả bé trai và bé gái đều thấy đúng).
- Mỗi nhân vật: 1 tư thế chính (full body) + 1 tư thế "chào" cho màn hình kết quả. Nền trong suốt.
- Không dùng font khác ngoài SVN-Gilroy cho chữ trong hình.

File giao:
- PNG nền trong suốt, cạnh dài 1200px, mỗi nhân vật 2 tư thế → 8 file.
- WebP tối ưu cho web, cạnh dài 600px → 8 file.
- File nguồn (AI/Figma).
- Đặt tên: `img_disc_D_main.webp`, `img_disc_D_wave.webp`, tương tự cho I/S/C.

## 3. Hạng mục B — Thẻ kết quả (share card)

Mục đích: PH bấm "Lưu thẻ kết quả" → nhận 1 ảnh để đăng story/feed. Người khác thấy ảnh phải hiểu ngay đây là trò gì và vào đâu để làm.

Hiện web tự vẽ thẻ bằng code (xem file `card.png` kèm brief). Cần creative làm lại thành template đẹp hơn, giữ đúng bố cục để dev thay vào:

Bố cục (kích thước 1080×1350, tỉ lệ 4:5 cho feed; thêm bản 1080×1920 cho story):
1. Góc trên trái: logo YOLA (file gốc trong `assets/img_logo_blue.png`, không hotlink).
2. Góc trên phải: nhãn "NHÓM D/I/S/C".
3. Giữa: nhân vật của nhóm, to, chiếm ~35% chiều cao.
4. Dòng "[Tên bé] là" nhỏ, rồi tên nhóm to.
5. 1 câu mô tả ngắn (tagline, đã có trong web).
6. Biểu đồ 4 thanh ngang (điểm 4 nhóm, tối đa 12).
7. Chân thẻ: "Con bạn thuộc kiểu học nào? Test 5 phút tại uudai.yola.vn/phong-cach-hoc-cua-con".

Yêu cầu:
- 4 phiên bản màu nền theo 4 nhóm (màu nhạt: `#FFF0EC`, `#FFF8D6`, `#EFFBE3`, `#E7F5FE`).
- Vùng chữ động (tên bé, tên nhóm, điểm) để trống, dev sẽ điền bằng code. Giao kèm file spec vị trí (x, y, font-size).
- Không có giá, không có ưu đãi, không có CTA bán hàng trên thẻ.

File giao: PNG nền (không chữ động) 4 nhóm × 2 tỉ lệ = 8 file + file spec vị trí + file nguồn.

## 4. Hạng mục C (phụ) — OG image + ảnh ads
- OG image 1200×630: 4 nhân vật đứng cạnh nhau + tiêu đề "Con bạn thuộc kiểu học nào?" + "Test 5 phút · Miễn phí".
- Bộ ads FB/GG (1:1, 4:5, 9:16): mỗi mẫu là 1 nhân vật + câu hỏi kiểu "Con hay xung phong hay hay ngại?" Marketing sẽ gửi copy ads riêng sau khi có nhân vật.

## 5. Không làm
- Không vẽ nhân vật giống mascot của trung tâm khác.
- Không thêm chữ "DISC" to trên hình (chỉ ghi nhỏ ở chú thích cuối web).
- Không thêm hiệu ứng 3D, gradient nặng. Giữ phẳng như bộ mascot voi.

## 6. Mốc
- Ngày 2: 4 sketch đen trắng + 2 hướng phong cách → Marketing chốt trong ngày.
- Ngày 5: bản màu đủ 4 nhân vật + 1 thẻ mẫu.
- Ngày 7: giao đủ file.
