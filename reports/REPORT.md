# Mẫu tham khảo để điền REPORT.md

**Cách dùng:** Bản cần nộp đã có sẵn ở [`REPORT.md`](../REPORT.md) trong thư mục gốc của fork; mở file đó và điền vào chỗ `…`. File này giải thích từng mục và có ví dụ để tham khảo khi bạn bị kẹt. Giữ nguyên bốn mục và bảng để coach đọc bài nhanh; **không chép ví dụ thành câu trả lời của mình**.

- Mã học viên theo lớp: 2A202602083
- Ngày / CVAT local: 17/09/2026 / CVAT local
- Công cụ đã dùng: Brush / Polygon

Mã học viên là mã lớp cấp, không cần ghi họ tên trong bản nộp nếu kênh lớp đã nhận diện bạn. Ở dòng công cụ, giữ lại những công cụ bạn thật sự dùng; không có SAM cũng hoàn toàn bình thường.

## 1. Bài đã nộp

**Bạn cần điền gì?** “File ZIP đúng tên” là tên file bạn đã tải từ CVAT rồi đặt lại, ví dụ `easy_semantic.zip`. “Hoàn thành mấy ảnh” là số ảnh bạn đã vẽ và Save, không phải số ảnh có trong task. Chưa làm hoặc export lỗi thì ghi `chưa có`, đừng ghi tên một ZIP rỗng. Cột điểm là **điểm tối đa của task**, không phải điểm tự chấm.

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

Không tự điền điểm nếu chưa có phản hồi từ người chấm. Nếu export lỗi, ghi task, trạng thái Save và thông báo đã gửi coach.

Ví dụ cách ghi lỗi export: “`cp3_thin`: đã Save 1/1 ảnh, CVAT không hiện Segmentation mask 1.1 lúc 14:10, đã báo coach”. Bạn vẫn ghi đúng tình trạng, không tự đổi format.

## 2. Một quyết định trước khi dùng gợi ý

**Mục này hỏi cách bạn tự ra quyết định.** Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi mở bất kỳ đề xuất tự động nào cho object đó. “Vị trí” chỉ cần mô tả đủ để tìm lại, chẳng hạn “xe bên trái, nửa dưới ảnh”; nếu nhớ tên file JPG thì ghi luôn. “Quy tắc biên” nghĩa là lý do bạn dừng mask ở đâu, nhất là mép ảnh hoặc vật che. Không cần ảnh chụp riêng nếu lớp không yêu cầu.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000458325.jpg`, xe ở phía trái gần giữa ảnh, object đầu tiên tôi vẽ là một chiếc xe ô tô.
- Class và quy tắc tôi dùng để chọn biên: class `car`. Tôi chỉ vẽ phần thân xe còn nhìn thấy, dừng mask ở mép vật và nơi bị che bởi cột hoặc khoảng trống, không đoán phần khuất phía sau. Nếu mép ảnh cắt mất một nửa vật, tôi dừng ở ranh nhìn thấy và không kéo ra nền.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: không dùng.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình. Tôi chọn `car` vì phần hình dạng rõ ràng, tường và mặt đường là nền, còn body xe có bề mặt sáng rõ hơn; tôi không gán vào `truck` vì không có chiều dài hoặc phần thùng đặc trưng đủ để xác nhận.

Ví dụ cách giải thích, không phải đáp án cho ảnh của bạn: “Tôi chỉ vẽ phần thân xe còn nhìn thấy; phần sau cột bị che nên không đoán đường biên phía sau.” Nếu công cụ đưa vùng tràn ra nền, hãy ghi đã xóa vùng nào và vì sao. “Gợi ý đúng” cũng cần nói bạn đã kiểm điều gì rồi mới giữ.

## 3. Một lỗi tôi tìm thấy và sửa

**Chọn một lỗi có thật trong bài của bạn**, không cần lỗi lớn nhất. Một dòng tốt có thể là: “Tại `cp2_slice`, hai xe cùng lớp bị gộp thành một mask; nhìn thấy khe giữa hai xe; tôi tách thành hai object, Save và export lại.” Nếu chưa sửa được do công cụ lỗi, nói rõ đã thử gì và cần coach hỗ trợ gì; đừng ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `cp2_slice`; vùng giữa hai xe sát nhau trong ảnh chính của task.
- Lỗi thuộc loại: gộp-tách.
- Bằng chứng tôi nhìn thấy: khe giữa hai xe rõ hơn so với một vật duy nhất, nếu không tách sẽ trở thành một mask lớn.
- Quy tắc và hành động sửa: tôi giữ nguyên quy tắc “hai xe sát nhau vẫn là hai instance”, chia mask thành hai vùng riêng, giữ ranh giữa chúng và loại bỏ vùng chồng lấn thừa.
- Sau sửa đã Save và export lại chưa? Có, đã Save và export lại sau khi tách mask.

**Nếu đã xem điểm tự đánh giá trên GitHub Actions hoặc chạy scorer:** ghi một kết quả liên quan lỗi bạn vừa sửa, chẳng hạn “`easy_semantic`: per-class IoU của `sidewalk` tăng sau khi tôi sửa ranh bó vỉa, Save và export lại”; nếu chưa có điểm, ghi “chưa có”. Xem [hướng dẫn xem Summary hoặc chạy dự phòng](../docs/SELF_SCORING.md). Kết quả ba tier là tổng **/82**, không tự điền PASS, top 3 hoặc bonus. Đừng đưa ground truth vào fork. Chưa có.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

**“Ca” là một vùng cụ thể khiến bạn phải dừng lại và chọn cách hiểu**, không nhất thiết là ba lỗi. Với mỗi dòng, ghi vị trí, hai khả năng bạn đã cân nhắc, dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi quyết định của bạn. Nếu quy tắc chưa đủ rõ, viết một câu hỏi mà coach có thể trả lời. Ví dụ: “mép bó vỉa trong `cp4_curb`: road hay sidewalk? Tôi chọn sidewalk vì phần nền nâng cao; xin xác nhận ranh tại chỗ màu giống mặt đường.” Ba dòng có thể đến từ ba task khác nhau.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `cp4_curb` - mép vỉa ở sát đường | road hoặc sidewalk | nền nâng cao và đường đi ở dưới, ranh gắn với chức năng vật lý hơn là màu | Tôi chọn `sidewalk` ở phần cao hơn, giữ ranh theo bó vỉa và không kéo ra đường bằng màu sắc. |
| `cp3_thin` - cột/biển ở vùng mảnh | phần này là background hay object có class riêng | kích thước mảnh, đường viền rõ, không được phủ tràn sang nền | Tôi giữ object theo phần hình dạng nhìn thấy, zoom lớn để tránh brush quá dày. |
| `cp2_slice` - giữa hai xe sát nhau | một mask gộp hai xe hoặc hai instance riêng | có khe hẹp giữa hai vật và đường viền tách rõ | Tôi chọn hai instance riêng, vì quy tắc task yêu cầu tách vật sát nhau dù cùng lớp. |
