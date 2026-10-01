---
description: Chuyển đổi và áp dụng phong cách trả lời (Concise, Executive Summary, Senior Architect, Tutor, Code-First).
---

# Format Response Command

Sử dụng lệnh này để chọn hoặc áp dụng định dạng câu trả lời mong muốn cho lượt tương tác hiện tại hoặc toàn bộ phiên làm việc.

## Các tùy chọn phong cách:

1. **`concise`**: Ngắn gọn, súc tích, đi thẳng vào kết quả/mã nguồn.
2. **`executive`**: Báo cáo tổng quan, đánh giá rủi ro và hành động tiếp theo.
3. **`architect`**: Đánh giá kiến trúc hệ thống, phân tích trade-offs và giải pháp tối ưu.
4. **`tutor`**: Giải thích từng bước, ẩn dụ dễ hiểu và đưa ra gợi ý học hỏi.
5. **`code-first`**: Trả lời ưu tiên mã nguồn runnable, giảm thiểu văn bản giải thích.

## Hướng dẫn xử lý:
1. Đọc yêu cầu hoặc tham số đi kèm lệnh (VD: `/format-response concise` hoặc `/format-response architect`).
2. Nếu người dùng không chỉ định tham số, hiển thị danh sách phong cách để người dùng lựa chọn.
3. Điều chỉnh phản hồi tiếp theo tuân thủ theo đúng quy chuẩn được định nghĩa trong Skill `response-formatting`.
