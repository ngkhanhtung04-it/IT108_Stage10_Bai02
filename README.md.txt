
# HƯỚNG DẪN CÀI ĐẶT CẢM BIẾN ĐỘ ẨM CHO TRANG TRẠI LAN

## 1. Giới thiệu

Tài liệu này hướng dẫn cài đặt và kiểm tra cảm biến độ ẩm đất để tự động điều khiển máy bơm nước cho trang trại Lan.

Hệ thống sử dụng cảm biến để đọc độ ẩm đất. Khi đất quá khô, chương trình sẽ bật máy bơm. Khi độ ẩm đạt mức yêu cầu, máy bơm sẽ tắt.

## 2. Chuẩn bị thiết bị

Các thiết bị cần chuẩn bị:

- Cảm biến độ ẩm đất.
- Bo mạch điều khiển có hỗ trợ Python.
- Máy bơm nước.
- Dây kết nối và nguồn điện phù hợp.

## 3. Cài đặt hệ thống

### 3.1. Kiểm tra Python

Mở Terminal và nhập lệnh sau để kiểm tra phiên bản Python:

```bash
python --version
```

Nếu hệ thống hiển thị phiên bản Python, bạn có thể tiếp tục cài đặt các thư viện cần thiết.

### 3.2. Các biến và câu lệnh quan trọng

- `soil_moisture`: biến lưu giá trị độ ẩm đất.
- `THRESHOLD`: ngưỡng độ ẩm để điều khiển máy bơm.
- `pump_on()`: hàm bật máy bơm.
- `pump_off()`: hàm tắt máy bơm.

## 4. Code Python điều khiển máy bơm

Ví dụ minh họa logic điều khiển máy bơm dựa trên độ ẩm đất:

```python
THRESHOLD = 30

def control_pump(soil_moisture):
    if soil_moisture < THRESHOLD:
        print("Dat kho, bat may bom")
        pump_on()
    else:
        print("Do am dat da du")
        pump_off()

def pump_on():
    print("May bom dang bat")

def pump_off():
    print("May bom da tat")

soil_moisture = 25
control_pump(soil_moisture)
```

Lưu ý: Đây là code minh họa. Khi sử dụng thiết bị thật, cần bổ sung thư viện và cấu hình chân điều khiển phù hợp với bo mạch. Không kết nối máy bơm trực tiếp vào chân GPIO; cần sử dụng mạch điều khiển phù hợp.

## 5. Bảng so sánh cảm biến

| Tiêu chí | Cảm biến loại cũ | Cảm biến loại mới |
|---|---|---|
| Nguyên lý | Đo độ ẩm bằng điện trở | Đo độ ẩm bằng điện dung |
| Khả năng chống ăn mòn | Thấp hơn | Tốt hơn |
| Độ ổn định | Có thể giảm theo thời gian | Thường ổn định hơn |
| Chi phí | Thường thấp | Thường cao hơn |
| Bảo trì | Có thể cần thay thế sớm | Thường ít bị ăn mòn hơn |

Lưu ý: Đây là so sánh tổng quát giữa cảm biến điện trở và cảm biến điện dung. Thông số thực tế phụ thuộc vào từng model.

## 6. Danh sách kiểm tra thiết bị

- [ ] Đã chuẩn bị đầy đủ cảm biến, bo mạch và máy bơm.
- [ ] Đã kiểm tra phiên bản Python.
- [ ] Đã kết nối cảm biến đúng sơ đồ.
- [ ] Đã kiểm tra giá trị độ ẩm đất.
- [ ] Đã thử logic bật máy bơm khi đất khô.
- [ ] Đã thử logic tắt máy bơm khi độ ẩm đạt yêu cầu.
- [ ] Đã kiểm tra nguồn điện và các kết nối an toàn.

## 7. Quy tắc Markdown cần nhớ

- Dùng `**nội dung**` để in đậm.
- Dùng `*nội dung*` để in nghiêng.
- Dùng dấu `#` kèm khoảng trắng để tạo tiêu đề.
- Dùng dấu `\` trước ký tự đặc biệt khi cần hiển thị ký tự đó theo nghĩa đen, ví dụ `\*` hoặc `\#`.
- Dùng dấu huyền ngược đơn cho Inline Code, ví dụ `python --version`.
- Dùng ba dấu huyền ngược và tên ngôn ngữ để tạo Code Block có Syntax Highlighting.
