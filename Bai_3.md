# BÀI 3: SỬ DỤNG AI AN TOÀN KHI XỬ LÝ LỖI PHẦN MỀM

#### ***Sinh viên: Võ Xuân Thịnh – Lớp CNTT2-K26***

## 1. Tình huống của mình

Mình cài Python thì gặp lỗi **"Path not found"**. Mình hỏi AI, nó đưa ra một câu lệnh bảo dán thẳng vào Terminal. Câu lệnh này trông lạ, lại có vẻ **can thiệp sâu vào hệ thống** (ví dụ sửa biến PATH của cả máy).

Vấn đề: AI có thể bị **Hallucination**, tức là bịa ra lệnh không có thật hoặc sai phiên bản hệ điều hành. Dán bừa vào Terminal thì có thể làm hỏng máy. Vì vậy mình **không chạy ngay**, mà kiểm chứng trước.

## 2. Báo cáo phân tích theo mô hình IPO


|                       | Nội dung                                                                                                                       |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Input**(đầu vào) | Câu trả lời của AI: câu lệnh lạ cần dán vào Terminal. Mình **chưa tin** , coi nó như thông tin cần kiểm tra. |
| **Process**(xử lý)  | Quy trình kiểm chứng 4 bước, xem bên dưới.                                                                              |
| **Output**(đầu ra)  | Kết luận: lệnh**an toàn** hay **không an toàn**, rồi mới quyết định chạy hay bỏ.                                 |

**Quy trình kiểm chứng (Process):**

1. **Tìm trên StackOverflow** bằng toán tử `site:`:

   ```
   site:stackoverflow.com "Python" "not recognized" PATH Windows
   ```

   Nếu nhiều người dùng đúng lệnh này và được chấm Likes cao, lệnh đáng tin.
2. **Đối chiếu trang chủ**`python.org` (mục Docs/Windows): xem cách chính thức xử lý lỗi PATH. Thường chỉ cần tích ô **"Add Python to PATH"** khi cài đặt.
3. **Kiểm tra lệnh có thật không:** tra từng thành phần của lệnh. Lệnh nào không thấy ở đâu ngoài câu trả lời của AI thì nghi ngờ bị bịa.
4. **Kiểm tra phiên bản hệ điều hành:** lệnh có đúng cho Windows của mình không, hay là lệnh của Linux/macOS.

**Kết luận (Output):**

* Lệnh có trên StackOverflow hoặc tài liệu chính thức, đúng hệ điều hành → **an toàn**, chạy được.
* Lệnh không tìm thấy ở nguồn nào, xóa/ghi đè sâu vào hệ thống, hoặc tải file từ link lạ → **không an toàn**, **không chạy**.

## 3. Prompt "hỏi ngược lại" AI

Mình gửi cho AI trước khi chạy lệnh:

```
Trước khi tôi chạy lệnh bạn vừa đưa, hãy trả lời giúp tôi:
1. Lệnh này làm gì, từng phần của lệnh có ý nghĩa gì?
2. Nó có thay đổi, xóa hay ghi đè gì trên hệ thống của tôi không?
3. Nó có an toàn trên Windows không? Mức rủi ro: thấp, trung bình hay cao?
4. Bạn có chắc lệnh này tồn tại thật không? Cho tôi link tài liệu chính thức hoặc câu hỏi StackOverflow để tôi tự kiểm tra.
5. Có cách nào an toàn hơn, ví dụ làm bằng giao diện thay vì gõ lệnh?
Nếu bạn không chắc, hãy nói thẳng là không chắc, đừng đoán.
```

**Vì sao prompt này hiệu quả:** nó bắt AI giải thích lệnh, nêu rủi ro, đưa nguồn để mình tự kiểm, và cho phép AI nói "không chắc" thay vì bịa.

## 4. Tóm tắt 3 dòng

* **IPO:** Input là câu trả lời AI → Process là kiểm chứng bằng `site:stackoverflow.com` và trang chủ → Output là kết luận an toàn hay không.
* **Không tin AI 100%**, vì AI có thể bịa lệnh (Hallucination).
* **Hỏi ngược lại AI** để nó giải thích rủi ro và đưa nguồn, rồi **tự kiểm chứng** trước khi chạy.
