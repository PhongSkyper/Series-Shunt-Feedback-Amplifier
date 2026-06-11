# Thiết kế Mạch Khuếch Đại FET Hồi Tiếp Âm Series-Shunt

Đây là kho lưu trữ chứa bộ mã nguồn chạy mô phỏng trên **LTspice** và các tài liệu liên quan đến Báo cáo Bài tập lớn môn **Mạch điện tử nâng cao (EE3205)** tại trường Đại học Bách Khoa - ĐHQG TP.HCM.

## 👥 Thông tin Nhóm thực hiện
- **Nhóm:** 05 - **Lớp:** L02
- **Thành viên:** Hà Minh Châu, Trương Đào Đan Huy, Nguyễn Thanh Phong, Lê Quang Tùng

---

## 🎯 1. Mục tiêu và cơ sở lý thuyết
- **Mục tiêu thiết kế:** Xây dựng mạch khuếch đại điện áp 2 tầng sử dụng MOSFET loại `2N7002` với hệ số khuếch đại vòng kín ổn định ở mức khoảng **20 dB** (~10 lần). Mạch được thiết kế nhằm mục đích mở rộng băng thông, tăng trở kháng vào, giảm trở kháng ra và đảm bảo hoạt động cực kỳ ổn định.
- **Cơ sở lý thuyết:** Cấu trúc hồi tiếp âm **Series-Shunt** (nối tiếp tại ngõ vào, song song tại ngõ ra) là cấu hình lý tưởng nhất cho một điện áp khuếch đại (Voltage Amplifier), giúp đạt được sự ổn định độ lợi, mở rộng dải tần và phối hợp trở kháng tối ưu.

## 📐 2. Thiết kế và tính toán lý thuyết
- **Linh kiện tích cực:** Sử dụng 2 MOSFET cực máng kênh N loại `2N7002` (chế độ tăng cường) có điện áp ngưỡng thấp, tốc độ đáp ứng rất nhanh.
- **Phân cực một chiều (DC):** Mạch được tạo bởi 2 tầng khuếch đại Source chung (Common Source) ghép trực tiếp hoặc thông qua tụ, trong đó điểm làm việc tĩnh (Q-point) được chọn là $I_D =$ **2 mA**, hỗ dẫn $g_m \approx$ **20 mS**. Chế độ hoạt động lúc này khuếch đại sâu vùng bão hòa với $V_{DQ} \approx$ 2.8 V.
- **Mạng hồi tiếp:** Lấy mẫu điện áp tại ngõ ra đi qua mạng phân áp song song để đưa điện áp mồi về ngõ vào. Để đạt được độ lợi hệ thống xấp xỉ 10 lần, điện trở hồi tiếp $R_f = 9.1\text{ k}\Omega$ và điện trở cực nguồn $R_s = 1\text{ k}\Omega$ được thiết kế, mang lại hệ số hồi tiếp $\beta \approx 0.099$.

## 💻 3. Kết quả mô phỏng (LTspice)
Mạch được mô phỏng chi tiết dưới hai cấu hình (Vòng hở và Vòng kín) để đối sánh trực tiếp tính hiệu quả của hồi tiếp âm:

| Thông số | Mạch Vòng Hở (Open-loop) | Mạch Vòng Kín (Closed-loop) | Hiệu quả & Phân tích |
| :--- | :--- | :--- | :--- |
| **Độ lợi điện áp** | **51.83 dB** ($\approx$ 391 lần) | **19.45 dB** ($\approx$ 9.38 lần) | Ổn định và sát với mục tiêu thiết kế lý thuyết 20 dB. |
| **Băng thông (BW)** | **11.27 kHz** | **323 kHz** | Mở rộng băng thông lên gần **29 lần**. |
| **Trở kháng vào** | **25.76 kΩ** | **25.81 kΩ** | Duy trì ở mức cao lý tưởng. |
| **Trở kháng ra** | **5.175 kΩ** | **109 Ω** | Giảm mạnh khoảng **47 lần**, hỗ trợ rất hiệu quả cho phối hợp tải. |

## 🛠 4. Thi công phần cứng và đo lường
Mạch đã được tiến hành cắm ngay trên test board với $V_{CC}=14.98\text{ V}$, $v_{in(\text{p-p})}=112\text{ mV}$.
- **Với Vòng hở:** Hiệu suất rất kém, chỉ đạt độ lợi thực tế ~75 lần do tác động của trở kháng ký sinh và nhiễu cộng hưởng trên test board.
- **Với Vòng kín:** Độ lợi đo đạc là 22.8 lần. Đặc biệt là dạng sóng xuất tại osciloscope hoàn toàn mượt mà. Tổng méo hài điện áp (**THD**) giảm cực hạn từ **4.5%** xuống chỉ còn **0.12%**, một minh chứng rõ ràng và điển hình cho sức mạnh tuyến tính của đường truyền hồi tiếp giảm méo dạng điện áp.

## 🔮 5. Tổng kết và Hướng phát triển
- **Đánh giá:** Rõ nét hóa công năng thực tế cũng như sức mạnh của khối kỹ thuật khuếch đại kết hợp hồi tiếp như ổn định, giảm méo điện áp và dải phổ rộng lớn hơn.
- **Tiềm năng phát triển:** Báo cáo mở ra đề xuất phát triển về việc sử dụng cấu trúc **Cascode** giúp siêu tối ưu hoá băng thông. Một đường nhánh tụ chặn điện áp một chiều (AC-coupled bypass pass) cũng được gợi ý tích hợp bên trong line hồi tiếp đảm bảo điểm làm việc (Q-Point) của mạch ít lệch đi dưới bất chấp dòng hồi tiếp nào.

---

## 📁 Cấu trúc thư mục & Cách chạy mô phỏng
Để mở và chạy các file sơ đồ, bạn cần phần mềm [LTspice Simulator](https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html).

### Danh sách các file dự án:
- `Nhóm05-L02-BTL MDTNC (Series-Shunt_feedback).asc`: Mạch chế độ có hồi tiếp (Closed-loop).
- `Nhóm05-L02-BTL MDTNC (Series-Shunt_nofeedback).asc`: Mạch chế độ không đường hồi tiếp (Open-loop).
- Kèm theo các file bản sao lưu dự phòng (`- Copy.asc`) và tài liệu Báo cáo (`.pdf`), present (`.pptx`).

### Hướng dẫn sử dụng:
1. Setup/Clone repository này: `git clone https://github.com/PhongSkyper/Series-Shunt-Feedback-Amplifier.git`
2. Sử dụng LTspice Simulator. Mở File (`.asc`) thông qua phần mềm.
3. Kích hoạt Run và đọc thông số điểm trên sơ đồ hoặc biểu đồ xuất ra dựa vào các lệnh đã khai báo có sẵn bên trong mạch gốc:
   - Các lệnh đã nạp `.op`, `.tran 0.001`, `.ac dec 100 1 100meg`.
