# Danh sách lớp v0 - Phan Lê Hoàng Phúc - G08

Viết tiếp từ slide bài giảng. Mỗi lớp làm rõ: model cần nhận ra cái này để làm gì?

## Hệ thống giám sát tài xế DMS

| STT | Lớp và thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | Trạng thái mắt eye_state | open, closed, unknown | Phát hiện trạng thái ngủ gật Drowsiness Detection khi thời gian mí mắt nhắm PERCLOS vượt ngưỡng an toàn. | Nhìn thấy được, trừ trường hợp tròng kính bị đốm lóa phản xạ đèn NIR che khuất. |
| 2 | Vùng nhìn gaze_zone | road, mirror_l, mirror_r, mirror_c, cluster, center, lap, other | Phát hiện mất tập trung thị giác Visual Distraction: cảnh báo khi người lái rời mắt khỏi làn đường phía trước quá 2 giây. | Nhìn thấy được qua hướng đầu và vị trí nhãn cầu trên ảnh IR. |
| 3 | Kính mắt glasses | none, clear, sun, unknown | Tinh chỉnh thuật toán ước lượng mắt: điều chỉnh mô hình khi có gọng kính che khóe mắt hoặc tròng kính làm khúc xạ ánh sáng. | Nhìn thấy được, nhưng kính râm tối màu có thể trông trong suốt dưới bước sóng 940nm. |
| 4 | Tay trên vô lăng hand_on_wheel | yes, no, unknown | Giám sát mức độ can thiệp điều khiển Hands-On Detection: nhắc nhở người lái giữ tay trên vô lăng khi xe đang bật chế độ lái hỗ trợ ADAS. | Phân biệt rõ hình dạng bàn tay và vành vô lăng. |
| 5 | Dùng điện thoại phone_interaction | held, mounted, lap, none | Phát hiện hành vi nguy hiểm làm phân tâm thao tác: cảnh báo người lái sử dụng điện thoại khi đang điều khiển phương tiện. | Nhìn thấy hình dạng hình học và độ phản xạ của viền và mặt kính điện thoại. |
| 6 | 13 điểm mốc mặt face13_landmarks | 13 tọa độ mí, khóe, mũi, miệng | Đo đạc chính xác tỉ lệ mở mắt EAR và tỉ lệ mở miệng MAR để phát hiện ngáp liên tục hoặc nhắm mắt li bì. | Ánh sáng NIR làm rõ các góc cạnh giải phẫu mặt ngay cả trong đêm tối. |

---

## Hệ thống giám sát khoang hành khách OMS

| STT | Lớp và thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | Người ngồi seat_occupancy | person: driver, front_pass, rear_left, rear_mid, rear_right | Kích hoạt túi khí thông minh theo vị trí có người ngồi và quản lý điều hòa nhiệt độ từng vùng Climate Control. | Hình dạng cơ thể người phản xạ tốt dưới ánh sáng hồng ngoại. |
| 2 | Trạng thái dây an toàn seatbelt_status | worn_correct, worn_incorrect, not_worn, unknown | Nhắc nhở thắt dây an toàn Seatbelt Reminder; điều chỉnh lực nổ túi khí tương ứng với tư thế thắt dây. | Nhìn thấy được nếu màu dây và áo tương phản; khó nhận biết nếu áo sẫm màu trùng màu dây. |
| 3 | Ghế trẻ em child_seat_presence | occupied: no, yes, unknown | Phục vụ hệ thống chống bỏ quên trẻ em trong xe Child Presence Detection; phát cảnh báo khẩn cấp qua còi xe hoặc ứng dụng điện thoại. | Nhận diện được hình khối cấu trúc của ghế trẻ em. |
| 4 | Hướng quay nôi em bé infant_seat_facing | facing: rear, front | Tự động tắt túi khí ghế trước nếu đặt nôi em bé quay ngược chiều để tránh chấn thương khi có va chạm. | Xác định được phần vòm che và quai xách của nôi trên ảnh IR. |
| 5 | Đồ vật bỏ quên leftover_object | bag, box, cup, other | Cảnh báo hành khách bỏ quên hành lý, balo khi rời xe; tránh hệ thống nhầm lẫn đồ vật nặng với trẻ em. | Nhận biết tốt qua hình dạng hình học và đường bao khối. |
| 6 | Ghế trống empty_seat | không vẽ hộp | Tối ưu hóa điều hòa và tiết kiệm năng lượng trên xe bằng cách tắt sưởi hoặc làm mát ở các vị trí ghế không có người. | Quan sát rõ toàn bộ bề mặt đệm và tựa lưng ghế trống. |

---

## Hai câu hỏi leo thang

### Câu hỏi 1:
- Câu hỏi: Trong trường hợp đồ vật như balo, túi xách được đặt trực tiếp bên trong lòng ghế an toàn trẻ em child_seat, mô hình OMS nên được thiết kế để phân loại toàn bộ cụm đó là một ghế trẻ em đang có vật cản, hay tách thành 2 lớp độc lập gồm child_seat và object?
- Khung hình ví dụ: Ảnh S01_rgb.png và S01_ir.png.
- Cách mình tạm gán và lý do: Mình tạm gán thành hai hộp riêng biệt gồm một hộp child_seat ôm trọn ghế và một hộp object ôm trọn đồ vật bên trong, cùng chung vị trí ghế. Lý do của mình là để giữ nguyên thông tin chi tiết cho cả hai thực thể, giúp mô hình học được ngữ cảnh ghế trẻ em chứa đồ vật chứ không phải chứa trẻ em, tránh báo động giả của hệ thống chống bỏ quên trẻ.

---

### Câu hỏi 2:
- Câu hỏi: Đối với ảnh hồng ngoại gần NIR trong khoang lái, khi tài xế đeo kính râm tối màu nhưng dưới bước sóng hồng ngoại 940nm tròng kính lại trở nên trong suốt nhìn thấy rõ mắt bên trong, thì thuộc tính glasses nên được gán theo kính râm đời thực glasses bằng sun hay gán theo hình ảnh thực tế camera thu được là glasses bằng clear hoặc unknown?
- Khung hình ví dụ: Ảnh D03.png.
- Cách mình tạm gán và lý do: Mình tạm gán là glasses bằng clear. Lý do của mình là mô hình thị giác máy tính học từ các điểm ảnh mà cảm biến ghi nhận được. Nếu dạy cho mô hình rằng một tròng kính hoàn toàn trong suốt là kính râm thì mô hình sẽ bị thiên lệch và nhầm lẫn khi phân loại các loại kính cận thông thường ngoài thực tế.
