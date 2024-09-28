# Winterwolf-Test
Bài test Winterwolf - IEC 

Đánh giá tổng quan về mặt project
- Với cách thiết kế, các script đều có mặt của GameManager, ví dụ như Board, nó sẽ gây ra vấn đề về việc module thấp hơn phụ thuộc module lớn hơn (Board không thể kéo sang game khác để sử dụng lại nếu thiếu GameManager). Board nên tương tác với bên ngoài bằng sự kiện hoặc là đưa các hàm hỗ trợ để Manager mode game đó sẽ có thể kiểm soát.  
- Chia thành phần rõ ràng hơn :
  + Bên ngoài menu : Riêng rẽ. Chỉ có nhiệm vụ hiển thị nút game mode, đồng thời chọn prefab game sinh ra cụ thể dựa trên mode chơi
  + Khi load game : Mỗi mode chơi có thể là 1 prefab, dựa trên mode được cung cấp bởi bên ngoài menu. Trong mode chơi sẽ tự xử lý logic win / lose. Mỗi 1 mode chơi sẽ có UI riêng chứ k switch case điều kiện. Lấy một ví dụ nếu tiếp tục phát triển, phát sinh thêm yêu cầu về mặt GD: Ngoài thời gian, số lượt match còn có thể là 1 item đặc biệt rớt bao nhiêu lần, hoặc là nhiều điều kiện khác (Tham chiếu Candy Crush Saga), thì việc cần phải chia mode game riêng rẽ ra là điều rất quan trọng. Nếu có những điều kiện khác nhau, board có thể dùng observer bắn các sự kiện cần thiết cho các mode chơi. Manager sẽ lắng nghe, dựa trên các điều kiện đó để kết thúc trò chơi, hoặc kiểm soát board để thực hiện một số hành động khác nhau 
  + Thêm các module khác riêng rẽ ở trong project : Module Data, Module Sound, Module Vibration, ....
