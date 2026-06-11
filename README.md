# Series-Shunt Feedback Amplifier Project (Mạch khuếch đại hồi tiếp nối tiếp - song song)

Đây là kho lưu trữ chứa các file mô phỏng LTspice cho Bài tập lớn môn Mạch điện tử nâng cao (MDTNC).
Dự án mô phỏng và phân tích mạch khuếch đại hồi tiếp với cấu hình Nối tiếp - Song song (Series-Shunt Feedback Amplifier).

## Thông tin Nhóm
- **Nhóm:** 05
- **Lớp:** L02
- **Môn học:** Mạch điện tử nâng cao (MDTNC)

## Cấu trúc và Phân tích nội dung các file
Dự án bao gồm các file schematic (`.asc`) được thiết kế trên LTspice để so sánh giữa hai trường hợp:

1. **Mạch không có hồi tiếp (Open Loop):**
   - `Nhóm05-L02-BTL MDTNC (Series-Shunt_nofeedback).asc`
   - Bản sao dự phòng: `Nhóm05-L02-BTL MDTNC (Series-Shunt_nofeedback - Copy).asc`

2. **Mạch có hồi tiếp nối tiếp - song song (Closed Loop):**
   - `Nhóm05-L02-BTL MDTNC (Series-Shunt_feedback).asc`
   - Bản sao dự phòng: `Nhóm05-L02-BTL MDTNC (Series-Shunt_feedback - Copy).asc`

## Yêu cầu phần mềm
Để mở, xem và chạy các file thiết kế, bạn cần cài đặt phần mềm **LTspice**. 
Đường dẫn tải xuống (nếu chưa có): [LTspice Download](https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html)

## Hướng dẫn sử dụng
1. Cài đặt LTspice trên máy.
2. Clone repository này về máy của bạn:
   ```bash
   git clone https://github.com/PhongSkyper/Series-Shunt-Feedback-Amplifier.git
   ```
3. Mở phần mềm LTspice, chọn `File` -> `Open` và mở các file `.asc` trong thư mục vừa tải về.
4. Bấm biểu tượng **Run** (hình người chạy) để chạy mô phỏng và phân tích mạch (DC op-amp, AC Sweep, Transient, tuỳ theo cấu hình có sẵn).
