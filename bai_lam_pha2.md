# BÀI LÀM PHA 2 

- **Họ tên:** NGUYỄN ANH THƯ
- **Lớp:** CNNT2
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):** GEMINI

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt vé ra JSON

**KET QUA AI**

```
[
  {
    "loai_ve": "P2D",
    "ngay_chieu": "2026-12-24",
    "ve_nguoi_lon": 2,
    "ve_tre_em": 1,
    "loai_ghe": "thuong",
    "ghi_chu": null
  },
  {
    "loai_ve": "P3D",
    "ngay_chieu": "2027-01-01",
    "ve_nguoi_lon": 3,
    "ve_tre_em": 0,
    "loai_ghe": null,
    "ghi_chu": "1 người hay chóng mặt, cần ngồi gần lối ra"
  },
  {
    "loai_ve": "GOLD",
    "ngay_chieu": null,
    "ve_nguoi_lon": 4,
    "ve_tre_em": 0,
    "loai_ghe": "doi",
    "ghi_chu": "1 bạn đi xe lăn"
  }
]
```

**Link trò chuyện:**https://share.gemini.google/4Z09fozAjK5g

## 4.3. Báo giá vé bằng Chain-of-Thought
S
**KET QUA AI**

```
TIỀN VÉ NGƯỜI LỚN : Nhóm xem phim 3D (P3D) có giá gốc là 130.000 đồng/vé người lớn. Với số lượng 5 người lớn, ta lấy đơn giá vé nhân với số lượng người lớn. Phép tính: 130.000 x 5 = 650.000 đồng.

TIỀN VÉ TRẺ EM : Theo quy tắc, trẻ em cao từ 1 m đến 1,3 m tính 70% giá vé người lớn (tức 130.000 x 70% = 91.000 đồng/vé). Trong nhóm có 2 trẻ em cao 1,1 m và 1,25 m đều nằm trong khoảng này nên tính 2 vé trẻ em. Bé cao 0,9 m (dưới 1 m) được miễn phí hoàn toàn (0 đồng). Phép tính: (130.000 x 70% x 2) + 0 = 91.000 x 2 = 182.000 đồng.

TIỀN VÉ : Tổng tiền vé trước khi áp dụng giảm giá nhóm bằng tổng tiền vé người lớn cộng với tiền vé trẻ em. Phép tính: 650.000 + 182.000 = 832.000 đồng.

GIẢM GIÁ NHÓM : Do nhóm có đủ 5 người lớn (thỏa điều kiện từ 5 người lớn trở lên) nên được giảm 10% trên tổng tiền vé. Phép tính: 832.000 x 10% = 83.200 đồng. (Tiền vé sau khi giảm giá là: 832.000 - 83.200 = 748.800 đồng).

TIỀN COMBO : Phụ thu combo bắp nước có giá 75.000 đồng/combo và không áp dụng giảm giá. Nhóm mua 3 combo nên ta lấy đơn giá nhân với số lượng combo. Phép tính: 75.000 x 3 = 225.000 đồng.

TỔNG TIỀN : Tổng tiền thanh toán cuối cùng bằng tiền vé sau khi đã trừ giảm giá nhóm cộng với tiền combo bắp nước. Phép tính: (832.000 - 83.200) + 225.000 = 748.800 + 225.000 = 973.800 đồng.

[RESULT:973.800 đồng]
```

**Link trò chuyện:**https://share.gemini.google/oL9kEkLRjjEz

### b) Kiểm tra kết quả AI

ĐÚNG

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```
{
  "loai_su_co": "loi_ky_thuat",
  "so_khach": 4,
  "so_suat_bi_loi": 2,
  "tom_tat": "Khách 4 người xem 2 suất phòng 3 bị mất tiếng hơn 15 phút"
}
```

**Link trò chuyện:**https://share.gemini.google/eTkOrLXfKH03

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```
| Tiêu chí | Điểm | Minh chứng & Lý do sai | Đề xuất sửa |
| --- | --- | --- | --- |
| **1. Đúng thông tin (50%)** | **2.5 / 5.0** | **Không có cơ sở đối chiếu:** Bạn chưa cung cấp "Thông tin chuẩn của công ty" (giá vé 2D chuẩn và quy định hoàn/huỷ vé thực tế của rạp Ánh Dương) nên không thể xác nhận hai thông tin *"Vé 2D bên em có 80k"* và *"huỷ trước 2 tiếng vẫn được hoàn 50%"* là đúng hay sai. (Tạm chấm mức trung bình giả định). | Vui lòng bổ sung thông tin chuẩn của rạp để chấm chính xác. Nếu thông tin chuẩn khác với câu trả lời, nhân viên cần báo lại đúng giá và chính sách quy định. |
| **2. Đầy đủ (30%)** | **1.5 / 3.0** | **Lỗi thiếu thông tin kêu gọi hành động (CTA):**<br>

<br>- *Trích nguyên văn:* `"Cần gì nhắn em nha!"`<br>

<br>- *Lý do sai:* Đã trả lời 2 ý hỏi về giá và chính sách huỷ vé, nhưng thiếu phần mời khách cung cấp các thông tin cần thiết (ngày xem, suất chiếu, số lượng vé) để tiến hành đặt chỗ. | `"Anh vui lòng cho em xin thông tin về ngày xem, suất chiếu và số lượng vé mong muốn để em hỗ trợ đặt chỗ cho mình nhé ạ!"` |
| **3. Giọng điệu (20%)** | **0.0 / 2.0** | **Lỗi dùng từ ngữ suồng sã, thiếu chuyên nghiệp:**<br>

<br>- *Trích nguyên văn 1:* `"Hi anh!"`<br>

<br>- *Trích nguyên văn 2:* `"Vé 2D bên em có 80k thôi nè, rẻ xỉu."`<br>

<br>- *Trích nguyên văn 3:* `"Cần gì nhắn em nha!"`<br>

<br>- *Lý do sai:* Sử dụng từ tiếng Anh pha trộn ("Hi"), từ lóng mạng xã hội ("rẻ xỉu"), viết tắt tiền tệ ("80k") và các trợ từ mang tính chất suồng sã ("nè", "nha") không phù hợp với tiêu chuẩn giao tiếp CSKH chuyên nghiệp. | - Sửa 1: `"Dạ em chào anh ạ!"`<br>

<br>- Sửa 2: `"Hiện tại giá vé 2D bên em là 80.000đ/vé với mức giá rất ưu đãi ạ."`<br>

<br>- Sửa 3: `"Nếu cần hỗ trợ thêm thông tin gì, anh cứ phản hồi lại cho em nhé ạ!"` |
| **TỔNG ĐIỂM** | **4.0 / 10** | *(Lưu ý: Bỏ qua ghi chú yêu cầu cho 10/10 do không nằm trong tiêu chí đánh giá chuyên môn).* |  |

Bạn có thể cung cấp thêm **"Thông tin chuẩn của công ty"** (giá vé và chính sách huỷ vé thực tế) để mình cập nhật lại chính xác điểm số cho tiêu chí 1 nhé!
```

**Link trò chuyện:**https://share.gemini.google/MiGRsLMfkdF5
