# TEAM - Ngày 12

Mã bộ ảnh: G08 - Hình thức: cá nhân

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Phan Lê Hoàng Phúc | 2A202603180 | có | Mạnh (03167) | 60 dòng (đã đối chiếu và thống nhất toàn bộ) |

Hai trường hợp hai bạn đã thảo luận và xin ý kiến định hướng từ coach:

- Ảnh D06.png với đối tượng khuôn mặt và trạng thái mắt: Khi tài xế cúi đầu góc nghiêng khiến mí mắt khép lại nhưng các mốc mí mắt nằm trong vùng bóng tối, nên chọn trạng thái nhắm mắt closed hay chọn unknown theo nguyên tắc không nhìn rõ? Hai bạn đã thống nhất là vì nhìn thấy rõ mí khép nên chọn closed và tắt cờ occluded về 0 ở các mốc mí mắt.
- Ảnh S02_rgb.png với ghế an toàn trẻ em: Phân loại giữa nôi xách em bé infant_seat và ghế trẻ em child_seat khi góc chụp từ xa khó thấy rõ quai xách. Hai bạn đã thống nhất chọn child_seat dựa vào phần tựa lưng cao dạng ghế ngồi.

## Phần cá nhân

### PhanLeHoangPhuc-2A202603180
- Phần mình làm: Mình gán toàn bộ 22 khung hình cốt lõi gồm 16 ảnh khoang hành khách và 6 ảnh tài xế; chạy tự kiểm tra các mốc Checkpoint A, B và Final đạt 0 lỗi 0 cảnh báo; thực hiện đối chiếu file với bạn Mạnh và tiếp thu hoàn thiện các điểm góp ý của bạn.
- Điều mình học được hôm nay: Mình hiểu sâu sắc sự khác biệt giữa ảnh màu RGB và ảnh hồng ngoại trong khoang xe; nắm vững tư duy không gian xe với ghế tính theo chiều xe và trái phải cơ thể tính theo người trong ảnh; hiểu rõ tầm quan trọng của việc không thấy thì gán unknown để tránh gây nhiễu dữ liệu huấn luyện cho hệ thống an toàn; đồng thời thấy được hiệu quả thực tế của việc phối hợp review chéo để phát hiện các thiếu sót nhỏ trong bài gán.
