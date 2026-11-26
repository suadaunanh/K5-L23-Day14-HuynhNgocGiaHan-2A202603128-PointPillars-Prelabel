# Báo cáo Day 14 — Huynh Ngoc Gia Han — 2A202603128

- Mã học viên dùng với `--student`: `128`
- `seed_tag` trong `frames_A.txt`: `393590736f`
- Tập A: `s01f59`, `s04f03`, `s05f22`
- Tập B: `s02f18`, `s02f34`, `s02f55`, `s03f07`, `s03f34`, `s03f51`, `s04f17`, `s04f32`, `s04f50`, `s05f15`, `s05f32`, `s05f48`

## 1. Dự đoán trước sweep (bước 5b)

Ghi **trước** khi chạy `scripts/pp_sweep.py`, rồi commit và push ngay (lịch sử commit là bằng chứng thời điểm viết). Không sửa phần này sau khi có kết quả.

- Tham số tôi nghĩ giảm công sửa nhiều nhất: Tôi nghĩ nên tăng tham số score_thr so với mức mặc định
- Vì sao (nhìn ảnh BEV tập A: box thừa nhiều hay box sót nhiều?): Box thừa quá nhiều, đặc biệt là tool model đánh sai cây thành cyclist và đánh thừa car khá nhiều. Tăng ngưỡng sẽ giúp tránh thừa box, đỡ thao tác xoá box.

## 2. Tập A: sửa tay và tune

Nhãn tham chiếu `ref_A.json`: 51 box (s01f59: 21, s04f03: 16, s05f22: 14). Cấu hình gốc dự đoán 102 box, khớp 50.

| Cấu hình           | Xóa | Thêm | Sửa | Chi phí |
| -------------------- | ---: | ----: | ---: | -------: |
| Gốc                 |   52 |     1 |   13 |     23.1 |
| `best_config.json` |      |       |      |          |

Chi tiết cấu hình gốc theo frame:

| Frame  | Xóa | Thêm | Sửa | Chi phí |
| ------ | ---: | ----: | ---: | -------: |
| s01f59 |   22 |     1 |    5 |     10.1 |
| s04f03 |    8 |     0 |    4 |      4.4 |
| s05f22 |   22 |     0 |    4 |      8.6 |

- Tham số đã đổi trong `best_config.json`: ...
- Kết quả leave-one-out (dán các dòng `scripts/pp_sweep.py` in ra): ...
- Cấu hình có ổn định trên từng frame không? Vì sao tôi vẫn chọn (hoặc không chọn) nó: ...

## 3. Trước/sau (bước 8)

![so sánh](<../../d14_128/compare/<frame>.jpg>)

- `scripts/pp_compare.py` báo giảm (hoặc tăng) ...% công sửa trên tập A.
- Dự đoán ở mục 1 đúng hay sai? Giải thích bằng số box xóa/thêm/sửa: ...

## 4. Tập B

Số đo từ `scripts/pp_prelabel.py --frames d14_128/frames_B.txt --config d14_128/best_config.json --gt d14_128/ref_B.json`:

| Xóa | Thêm | Sửa | Chi phí |
| ---: | ----: | ---: | -------: |
|      |       |      |          |

- Loại box tốn công sửa nhất ở tập B: ...

## 5. Giới hạn

- ...
- ...
