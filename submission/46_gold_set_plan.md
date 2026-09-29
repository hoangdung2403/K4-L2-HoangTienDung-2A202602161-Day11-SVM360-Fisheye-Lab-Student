# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn vừa vẽ.

> **Lưu ý:** GUIDE/template không quy định sẵn tỷ lệ normal/hard hay nội dung hard case cho từng camera. Bản dưới đây
> là một **đề xuất để điền TODO**: 50 frame/camera, gồm 35 normal + 15 hard, tổng đúng 200 frame. Các hard case nên
> được điều chỉnh nếu instructor/guide của lớp có rule cụ thể hơn.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Vật thể ở vùng biên/xa, che khuất, hình học fisheye khó | Box dễ lệch kích thước/vị trí và dễ bỏ sót object nhỏ | Giữ đúng camera front, calibration và annotation space đã chốt | Hai người review độc lập, đối chiếu ảnh gốc + rule; chỉ gọi gold sau khi xử lý disagreement |
| rear | Vật thể ở vùng biên/xa, che khuất, hình học fisheye khó | Góc nhìn phía sau có thể làm object nhỏ/khó quan sát và box dễ lệch | Giữ đúng camera rear, calibration và annotation space đã chốt | Review độc lập, đối chiếu ảnh gốc + rule; giải quyết disagreement trước khi chốt |
| left | Seam/vùng chuyển tiếp, vùng biên fisheye, object bị che khuất | Dễ nhầm object ở vùng chuyển tiếp và sai hình học gần biên ảnh | Giữ đúng camera left, calibration và annotation space; không tự ý ghép box qua seam | Review độc lập; case seam/cross-camera phải có policy và evidence trước khi ghép |
| right | Seam/vùng chuyển tiếp, vùng biên fisheye, object bị che khuất | Dễ nhầm object ở vùng chuyển tiếp và sai hình học gần biên ảnh | Giữ đúng camera right, calibration và annotation space; không tự ý ghép box qua seam | Review độc lập; case seam/cross-camera phải có policy và evidence trước khi ghép |

- **Khi nào cần refresh gold set:** Khi đổi camera, calibration hoặc annotation rule có thể làm thay đổi cách diễn giải
  object/box; khi đó cần xác định lại các case bị ảnh hưởng và review lại trước khi tiếp tục dùng gold set.
- **Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box:** Chỉ ghép khi có rule xác định object
  là cùng một instance và có bằng chứng từ các view/frame liên quan; nếu chưa đủ evidence thì giữ riêng và escalates
  để người soát quyết định.
- **Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera:**
  Vì mỗi camera có góc nhìn và vùng hình học/calibration khác nhau; agreement trên một camera không bao phủ các lỗi
  đặc thù của ba camera còn lại. Gold set phải được review theo từng camera và các hard case tương ứng.
