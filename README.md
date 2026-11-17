1. Thiết kế giải pháp (I/O)
Tên giải pháp: Tự động hóa xử lý đơn hàng tại cửa hàng.

Mục tiêu: Sử dụng AI để kiểm tra thông tin, tính tiền và phân loại trạng thái đơn hàng.

Input (Đầu vào):
- Mã đơn hàng.
- Tên khách hàng.
- Tên sản phẩm.
- Số lượng.
- Đơn giá.
- Trạng thái thanh toán.
Output (Đầu ra):
- Thông tin đơn hàng.
- Tổng tiền cần thanh toán.
- Trạng thái đơn hàng.
- Lỗi dữ liệu (nếu có).
- Hướng xử lý tiếp theo.
2. Quy trình xử lý (Prompt Chaining)
1. Bước 1: Kiểm tra dữ liệu thiếu hoặc sai.
2. Bước 2: Tính tổng tiền và kiểm tra thanh toán.
3. Bước 3: Xuất kết quả dưới dạng JSON.
Ứng dụng kỹ thuật:
- Chain-of-Thought: Kiểm tra logic theo từng bước.
- Prompt Chaining: Chia công việc thành nhiều giai đoạn.
- Context Management: Lưu trạng thái để tiếp tục khi bị gián đoạn.
3. Prompt thực thi
Bạn là trợ lý AI quản lý đơn hàng cửa hàng.

Nhiệm vụ:
1. Kiểm tra thông tin đơn hàng.
2. Tính tổng tiền = Số lượng × Đơn giá.
3. Xác định trạng thái thanh toán.
4. Xuất kết quả dưới dạng JSON.
Quy tắc:
- Nếu thiếu dữ liệu, báo NEEDS_INFO.
- Nếu số lượng hoặc đơn giá nhỏ hơn hoặc bằng 0, báo INVALID_DATA.
- Không tự ý đoán dữ liệu.
- Nếu chưa thanh toán, ghi trạng thái Chờ thanh toán.
- Lưu trạng thái xử lý để tiếp tục khi bị gián đoạn.
Input:
Mã đơn: DH001
Khách hàng: Nguyễn Văn A
Sản phẩm: Chuột máy tính
Số lượng: 2
Đơn giá: 150000
Thanh toán: Đã thanh toán.

Chỉ xuất JSON hợp lệ.




4. Kết quả chạy thử
{
  "order_id": "DH001",
  "customer": "Nguyễn Văn A",
  "product": "Chuột máy tính",
  "quantity": 2,
  "unit_price": 150000,
  "total": 300000,
  "payment_status": "Đã thanh toán",
  "order_status": "Hợp lệ",
  "error": [],
  "next_action": "Xác nhận đơn hàng"
}