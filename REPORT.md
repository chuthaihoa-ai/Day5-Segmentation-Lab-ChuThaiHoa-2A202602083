# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

- Mã học viên theo lớp: 2A202602083
- Ngày / CVAT local: 17/09/2026 / CVAT local
- Công cụ đã dùng: Brush / Polygon

## 1. Bài đã nộp

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

## 2. Một quyết định trước khi dùng gợi ý

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000458325.jpg`, xe ở phía trái gần giữa ảnh, object đầu tiên tôi vẽ là một chiếc xe ô tô.
- Class và quy tắc tôi dùng để chọn biên: class `car`. Tôi chỉ vẽ phần thân xe còn nhìn thấy, dừng mask ở mép vật và nơi bị che bởi cột hoặc khoảng trống, không đoán phần khuất phía sau. Nếu mép ảnh cắt mất một nửa vật, tôi dừng ở ranh nhìn thấy và không kéo ra nền.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: không dùng.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình. Tôi chọn `car` vì phần hình dạng rõ ràng, tường và mặt đường là nền, còn body xe có bề mặt sáng rõ hơn; tôi không gán vào `truck` vì không có chiều dài hoặc phần thùng đặc trưng đủ để xác nhận.

## 3. Một lỗi tôi tìm thấy và sửa

- Task/ảnh/vùng: `cp2_slice`; vùng giữa hai xe sát nhau trong ảnh chính của task.
- Lỗi thuộc loại: gộp-tách.
- Bằng chứng tôi nhìn thấy: khe giữa hai xe rõ hơn so với một vật duy nhất, nếu không tách sẽ trở thành một mask lớn.
- Quy tắc và hành động sửa: tôi giữ nguyên quy tắc “hai xe sát nhau vẫn là hai instance”, chia mask thành hai vùng riêng, giữ ranh giữa chúng và loại bỏ vùng chồng lấn thừa.
- Sau sửa đã Save và export lại chưa? Có, đã Save và export lại sau khi tách mask.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `cp4_curb` - mép vỉa ở sát đường | road hoặc sidewalk | nền nâng cao và đường đi ở dưới, ranh gắn với chức năng vật lý hơn là màu | Tôi chọn `sidewalk` ở phần cao hơn, giữ ranh theo bó vỉa và không kéo ra đường bằng màu sắc. |
| `cp3_thin` - cột/biển ở vùng mảnh | phần này là background hay object có class riêng | kích thước mảnh, đường viền rõ, không được phủ tràn sang nền | Tôi giữ object theo phần hình dạng nhìn thấy, zoom lớn để tránh brush quá dày. |
| `cp2_slice` - giữa hai xe sát nhau | một mask gộp hai xe hoặc hai instance riêng | có khe hẹp giữa hai vật và đường viền tách rõ | Tôi chọn hai instance riêng, vì quy tắc task yêu cầu tách vật sát nhau dù cùng lớp. |
