# Bài 9: Xây dựng Prompt 3 thành phần giải mã thông báo lỗi trạm sạc cùng trợ lý AI

## Phần 1: Xây dựng Prompt

### 1. Phân tích câu hỏi chưa tốt

Câu hỏi quá cụt, không có thiết bị, hệ điều hành hay lỗi cụ thể nên AI phải đoán mò. Thấy hỏng thì đoán là lỗi phần cứng. Đó là **ảo giác AI** (hallucination).

### 2. Prompt 3 thành phần

> **[Context]** Tôi trực trạm sạc VoltCharge số 04, máy chạy Windows 11, trụ đang sạc xe taxi điện thì dừng và hiện lỗi dưới đây.
>
> **[Raw Error]** `System.UnauthorizedAccessException: Access to the path 'C:\Program Files\VoltCharge\data\session.log' is denied. Process terminated with exit code 5.`
>
> **[Instruction]** Giải thích lỗi bằng tiếng Việt dễ hiểu và đưa ra 3 bước khắc phục.

---

## Phần 2: Đọc hiểu phản hồi của AI

### 3. Giải thích lỗi

Phần mềm muốn ghi file `session.log` vào thư mục Program Files nhưng không có quyền admin nên Windows chặn, phần mềm không chạy được. Đây là **lỗi phân quyền**, không phải hỏng phần cứng.

### 4. Ba bước khắc phục

- **Bước 1:** Chuột phải phần mềm VoltCharge, chọn **Run as administrator**.
- **Bước 2:** Chuột phải thư mục `data` → **Properties** → **Security** → **Edit**, cho tài khoản chạy phần mềm quyền **Write** và **Modify**, bấm **Apply**.
- **Bước 3:** Mở lại phần mềm và kiểm tra trụ 04 sạc lại được chưa.

### 5. Xử lý thông tin nhạy cảm (API key)

Phải **xóa hoặc thay bằng `[HIDDEN]`** trước khi dán. Vì API key là bí mật, gửi lên AI có thể bị lộ, rồi bị người khác dùng để xâm nhập hệ thống.
