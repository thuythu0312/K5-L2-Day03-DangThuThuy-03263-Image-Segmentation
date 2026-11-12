# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603263
- Ngày / CVAT local: 12/11/2026 tại http://localhost:8080/jobs
- Công cụ đã dùng: CVAT local và script inspect_submissions.py để kiểm tra ZIP

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

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
| Tổng tối đa | | | 100 |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở medium_instance, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: cần người làm xác nhận từ phiên thao tác ban đầu
- Class và quy tắc tôi dùng để chọn biên: điền sau khi xác định đúng đối tượng đầu tiên
- Nếu dùng gợi ý sau đó: cần xác nhận có dùng gợi ý và ghi lại thao tác thực tế
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi có thật trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: chưa xác minh được một lỗi đã sửa
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: chưa xác định
- Bằng chứng: cả 9 ZIP qua kiểm tra cấu trúc. Cần đối chiếu mask với ảnh gốc để xác định lỗi về biên, lớp hoặc phủ vùng
- Quy tắc và hành động sửa: ghi theo thao tác thực tế sau khi xác định lỗi
- Sau sửa đã Save và export lại chưa? Chưa xác minh.

Nếu bạn đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): chưa có điểm. Scorecard ba tier tối đa 82, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một vùng cụ thể khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| cp1_holes / 000000144300.jpg / vùng kính hoặc khoảng hở bên trong đường bao | Chi tiết của vật hoặc nền nhìn xuyên qua | Đối chiếu xem vùng đó là bề mặt kính hay một lỗ thật có nền lộ ra | Giữ kính trong mask, chừa lỗ nền thật. Cần kiểm biên trên lớp phủ |
| cp4_curb / 7d83710e-4697c3b2.jpg / mép tiếp giáp đường và vỉa hè | road hoặc sidewalk | Theo bó vỉa và chức năng của bề mặt, không dựa riêng vào màu | Kiểm lại đường biên mask dọc bó vỉa |
| cp5_occlusion / 000000336232.jpg / các phần nhìn thấy quanh vùng bị che | Hai vật riêng hoặc các phần của cùng một vật | Dựa vào đường nét và hướng của vật ở hai phía vùng che | Nếu xác định cùng vật thì giữ một ID và chỉ vẽ phần nhìn thấy |
