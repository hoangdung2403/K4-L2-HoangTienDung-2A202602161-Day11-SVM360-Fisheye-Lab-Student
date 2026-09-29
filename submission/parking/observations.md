# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ:
  - Vạch thứ nhất: vạch sơn màu vàng ở khu vực tiền cảnh, chạy chéo từ phía trái xuống khu vực giữa ảnh, dùng làm ranh giới giữa các ô đỗ.
  - Vạch thứ hai: vạch sơn màu vàng ở khu vực tiền cảnh, nằm về phía bên phải vạch thứ nhất, cũng tạo ranh giới giữa các ô đỗ.

- Một vạch/dấu sơn hoặc biên không vẽ, và vì sao:
  - Không gán nhãn các vạch dài nằm ngang theo hướng lối xe chạy ở phía xa, vì chúng không thể hiện rõ ranh giới của một ô đỗ riêng lẻ mà có vai trò phân chia/hướng dẫn khu vực lưu thông trong bãi.

- Polygon `free_space` dừng ở đâu; có phần bị che nào không:
  - Polygon `free_space` bao phủ phần mặt đường trống nhìn thấy của lối xe chạy ở khu vực phía trước các ô đỗ.
  - Polygon dừng theo các ranh giới nhìn thấy của mặt đường và không đi xuyên qua các khu vực bị vật thể che khuất.
  - Trong vùng đã gán nhãn không có phần bị che khuất đáng kể cần phải suy đoán.

- Ca chưa chắc cần hỏi người soát:
  - không có