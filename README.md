# PCB Bonus_ESP32 CAM Programming

Bo mạch hỗ trợ nạp chương trình cho ESP32-CAM (và các module ESP32 dùng UART), với khả năng Boot/Reset tự động, nút điều khiển thủ công, và mạch nguồn chuyển đổi từ +5V DC sang +3.3V DC an toàn.

## Tính năng
- Có chức năng Boot và Reset tự động.
- Có nút Reset và Boot để thao tác thủ công khi cần.
- Có mạch regulator từ +5V DC sang +3.3V DC.
- Hỗ trợ nạp code thông qua giao thức UART.

## Thông số kỹ thuật 
|  | Chi tiết |
|---|---|
| Điện áp đầu vào | +5V DC (USB type B) |
| Điện áp đầu ra | +3.3V DC, 3A |
| Giao thức nạp | UART |
| Tự động Boot/Reset | Thông qua DTR/RTS |
| Nút điều khiển | RST, IO0 |

## Sơ đồ nối dây
- 3V3 → 3V3.
- GND → GND.
- TXD của board → RX0 của ESP32-CAM.
- RXD của board → TX0 của ESP32-CAM.
- RST của board → EN của ESP32-CAM.
- IO0 của board → GPIO0 của ESP32-CAM.

## Hướng dẫn nạp code qua UART
### Cách 1: Tự động 
1. Kết nối board với máy tính, cài driver CH340.
2. Kết nối các chân.
3. Mở Arduino IDE/PlatformIO, chọn đúng cổng COM và loại Board.
4. Nhấn Upload.

### Cách 2: Thủ công 
1. Nhấn giữ nút IO0.
2. Nhấn nút RST, sau đó thả RST.
3. Thả nút IO0. ESP32 vào chế độ nạp, tiến hành Upload.

## Lưu ý thiết kế và sử dụng
1. Dây TX/RX phải bắt chéo: TX của board → RX của ESP32, RX của board → TX của ESP32.
