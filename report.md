## 1. So sánh thời gian chạy

| Tiêu chí                            | Lần chạy 1 (Cache Miss)           | Lần chạy 2 (Cache Hit)           | Tỷ lệ Tối ưu                        |
|:------------------------------------|:----------------------------------|:---------------------------------|:------------------------------------|
| **Trạng thái Cache**                | Chưa tồn tại (`miss`)             | Tồn tại sẵn (`hit`)              | -                                   |
| **Thời gian Setup Java & Caching**  | 4s                                | 7s (bao gồm restore cache)       | -                                   |
| **Thời gian Tải Dependencies**      | **1m 32s** (Download ~150MB libs) | **0s** (Đã nạp sẵn trong runner) | **Giảm 100% thời gian tải mạng**    |
| **Thời gian Thực thi Gradle Build** | 1m 48s                            | 18s                              | Giảm ~83%                           |
| **Tổng thời gian Job CI**           | **2m 12s**                        | **31s**                          | **Tăng tốc 4.25x (~76% nhanh hơn)** |

## 2. Nhận xét

Ở lần chạy thứ hai, kiểm tra log của bước `Set up Java 17` để xác nhận cache Gradle được khôi phục. Ghi nhận thời gian thực tế của hai lần chạy để đánh giá sự khác biệt.
