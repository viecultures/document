# 🎧 Luồng Âm Thanh Tự Nhiên & Nghe Chép Dictation (Natural Audio & Dictation)

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Interface: [`interface_reader.md`](./interface_reader.md)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md) (`AudioSpeeds`: `['1x', '0.8x', '0.5x']`)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`audio_timestamp_start`, `audio_timestamp_end`)

---

## 2. Trình Phát Âm Thanh Tự Nhiên (Sticky Audio Player)

1. **Vị trí & Bố cục:**
   - Cố định ở đầu trang hoặc đáy màn hình (Sticky Bottom/Top Bar).
   - Nút Play/Pause lớn, Seekbar thanh thời gian bài học, nút tua lùi 5 giây.
2. **Bộ điều khiển tốc độ đọc:**
   - Hệ thống cung cấp 3 nút chọn tốc độ nhanh: **`[1x]`**, **`[0.8x]`**, **`[0.5x]`** (theo đúng quy định bất biến tại `system_constants.md`).
3. **Phát âm thanh câu đơn (Sentence Audio):**
   - Khi người học bấm trực tiếp vào bất kỳ câu tiếng Anh nào trong bài đọc, hệ thống kích hoạt phát âm thanh của riêng câu đó (Shadowing mode) và tự động làm nổi bật viền câu đang phát.

---

## 3. Chế Độ Luyện Nghe Chép Chính Tả (Dictation Mode)

Mô phỏng cấu trúc trải nghiệm tương tác cao (như DailyDictation):

1. **Cấu trúc dữ liệu:**
   - Mọi câu đều có cặp mốc thời gian `audio_timestamp_start` và `audio_timestamp_end`.
2. **Cơ chế so khớp ký tự thời gian thực (Real-time Word Matching):**
   - Từ gõ đúng: Hiển thị màu **Xanh lá (`#2F855A`)**.
   - Từ gõ sai: Gạch chân màu **Cam (`#DD6B20`)** trực tiếp trong ô nhập liệu.
   - Từ chưa gõ: Che bởi ký tự đại diện (`*`).
3. **Tùy chọn trợ giúp:**
   - `[x] Show answer immediately`: Hiển thị gợi ý so sánh ngay khi gõ.
   - `[ ] Show full answer`: Hiện 100% đáp án câu khi người học gặp bế tắc.
   - Nút `[ Skip ]`: Bỏ qua câu để tiếp tục luồng học.
   - Nút Micro `[🎙️]`: Hỗ trợ nhập liệu bằng giọng nói thông qua Web Speech API.

```
DICTATION GIAO DIỆN TƯƠNG TÁC:
+-----------------------------------------------------------------------+
| [ Dictation ]   [ Full Transcript ]                 < 4 / 12 >        |
| [ ▶ Play 0:01/0:01 ] ----------------------------- [🔊] [ 1x ▾ ]      |
+-----------------------------------------------------------------------+
| I am cook dinner.                                                     |
|       ~~~~ (Gạch chân Cam)                                [🎙️] [Skip] |
+-----------------------------------------------------------------------+
| ⚠️ Incorrect                                                          |
| I am cooking *******                                                  |
| [x] Show answer immediately     [ ] Show full answer                  |
+-----------------------------------------------------------------------+
```
