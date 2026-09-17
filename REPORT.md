# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602083
- Ngày / CVAT local: 17/09/2026 / CVAT local
- Công cụ đã dùng: Brush / Polygon

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

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

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000458325.jpg`, xe ở phía trái gần giữa ảnh; object đầu tiên tôi tự vẽ là một chiếc `car`.
- Class và quy tắc tôi dùng để chọn biên: class `car`. Tôi chỉ giữ phần thân xe còn nhìn thấy, dừng mask ở mép vật và nơi bị che bởi cột hoặc khoảng trống; không đoán phần khuất phía sau. Nếu mép ảnh cắt mất vật, tôi dừng ở ranh nhìn thấy và không kéo ra nền.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: không dùng.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình. Tôi chọn `car` vì hình dạng thân xe rõ hơn nền và không thấy phần thùng dài như `truck`; tôi không mở rộng mask sang mặt đường hoặc tường.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `cp2_slice`; vùng giữa hai xe sát nhau trong ảnh task.
- Lỗi thuộc loại: gộp-tách.
- Bằng chứng tôi nhìn thấy: khe giữa hai xe vẫn rõ, nếu không tách sẽ thành một mask lớn và không đúng với quy tắc task.
- Quy tắc và hành động sửa: theo quy tắc task, hai xe cùng lớp nhưng sát nhau vẫn là hai instance; tôi tách mask thành hai vùng riêng, giữ ranh giữa hai xe và loại bỏ vùng chồng lấn thừa.
- Sau sửa đã Save và export lại chưa? Có, đã Save và export lại.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork. Chưa có.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `cp4_curb` - mép vỉa sát đường | road hoặc sidewalk | phần nền cao hơn và ranh gắn với chức năng bó vỉa hơn là màu sắc | Tôi chọn `sidewalk` ở phần cao hơn, giữ ranh theo bó vỉa và không kéo ra đường theo màu. |
| `cp3_thin` - cột/biển mảnh | background hoặc class riêng | phần mảnh có đường viền rõ, cần zoom lớn để tránh brush quá dày | Tôi giữ object theo phần nhìn thấy, không phủ lan sang nền. |
| `cp2_slice` - giữa hai xe sát nhau | một mask gộp hai xe hoặc hai instance riêng | quy tắc task nói hai xe cùng lớp sát nhau vẫn là hai instance | Tôi chọn hai instance riêng để tránh gộp mask. |
