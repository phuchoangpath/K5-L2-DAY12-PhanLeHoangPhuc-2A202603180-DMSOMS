# Tự đánh giá - Phan Lê Hoàng Phúc - G08

## 1. Tự rà soát 4 cảnh

Nghỉ tay một chút, mình mở lại bài đã gán và chọn ra 4 ảnh gồm 2 ảnh khoang sau OMS và 2 ảnh tài xế DMS để đọc lại thật kỹ như một người chấm bài độc lập.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb.png | person | seat_flip | Ban đầu mình để theo giá trị mặc định của phần mềm là driver, sau đó mình phát hiện ra và sửa lại thành rear_left theo đúng chiều xe. | Đã sửa |
| S05_ir.png | face | missing | Mình bị thiếu hộp khuôn mặt bên trong hộp người lớn theo quy định mục 4.2 của tài liệu hướng dẫn OMS, mình đã vẽ bổ sung đầy đủ. | Đã sửa |
| D05.png | hand | lr_flip | Ảnh chụp bị xoay 90 độ nên rất dễ nhầm tay trái và tay phải, mình đã rà soát lại theo cơ thể tài xế và chỉnh lại chính xác. | Đã sửa |
| D06.png | face13 | flag | Tài xế cúi đầu nhìn thấy rõ mí mắt khép lại, mình tắt cờ che khuất occluded về 0 ở các điểm mốc mí mắt để dữ liệu chuẩn xác và không bị cảnh báo logic. | Đã sửa |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi mình dễ mắc nhất hôm nay là quên chỉnh lại thuộc tính vị trí ghế khi vẽ một hộp mới trên công cụ gán nhãn, vì hệ thống luôn tự điền sẵn giá trị driver. Ngoài ra ở phần khoang sau, thỉnh thoảng mình vẽ xong người lớn mà quên vẽ kèm hộp khuôn mặt bên trong.

Nguyên nhân là do thói quen thao tác nhanh tay trên hàng ghế sau rồi chuyển sang ảnh khác mà chưa mở bảng chi tiết để kiểm tra lại thuộc tính, cũng như chưa chú ý kỹ quy tắc người lớn trong OMS luôn cần có cả hộp person và hộp face.

Cách mình khắc phục cho những lần sau: Mình tự tạo phản xạ là cứ vẽ xong người lớn ở khoang sau là vẽ ngay hộp mặt đi kèm, đồng thời mở ngay bảng thuộc tính để chọn đúng vị trí ghế theo xe rồi mới chuyển sang đối tượng tiếp theo.

## 3. Ghi chú về việc đối chiếu và tiếp thu ý kiến bạn Mạnh

Sau khi trao đổi và chạy so sánh với bạn Mạnh, bạn đánh giá cao các phân loại của mình ở ảnh S01_ir khi nhận diện không thắt dây an toàn, ảnh S03 nhận diện ba lô có quai xách, ảnh D01 nhận diện hướng nhìn đường, ảnh D05 xác định đúng tay trái tay phải và ảnh D06 nhận diện hướng nhìn cụm đồng hồ.

Đồng thời, mình đã tiếp thu toàn diện 4 điểm góp ý của Mạnh để hoàn thiện bộ nhãn:
1. Ảnh D06.png: Mình chuyển các điểm mốc mí mắt về trạng thái không bị che khuất occluded bằng 0 vì nhìn thấy rõ mí khép, giúp quá trình kiểm tra đạt kết quả hoàn hảo không lỗi và không cảnh báo.
2. Các ảnh S05 và S07 cả bản màu lẫn bản hồng ngoại: Mình bổ sung hộp khuôn mặt cho toàn bộ hành khách người lớn theo đúng quy chuẩn khoang sau.
3. Ảnh S02 ở ghế sau bên trái: Mình chuyển phân loại từ infant_seat thành child_seat có người ngồi occupied bằng yes theo đúng thống nhất chung về loại ghế tựa lưng cao.
4. Ảnh S05 mình chuyển thuộc tính ghế trẻ em sang không có người ngồi occupied bằng no; cập nhật ảnh D02 có thắt dây an toàn đúng cách worn_correct; và bổ sung hộp đồ vật chiếc cốc ở vị trí ghế giữa của ảnh S01.
