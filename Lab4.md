# **Thiết kế các ca sử dụng cho hệ thống Payroll System**
---
## 1. Maintain Timecard
#### Mô tả:
Cho phép nhân viên quản lý (thêm, chỉnh sửa) thời gian làm việc. Đây là cơ sở để tính toán lương.
#### Luồng sự kiện:
1. Tác nhân chính: Nhân viên.
2. Luồng chính:
    - Nhân viên đăng nhập vào hệ thống Payroll.
    - Nhân viên chọn chức năng "Maintain Timecard".
    - Nhân viên nhập thời gian làm việc hoặc chỉnh sửa thông tin đã nhập trước đó.
    - Hệ thống kiểm tra dữ liệu hợp lệ và lưu lại vào cơ sở dữ liệu.
3. Luồng phụ:
    - Nếu dữ liệu không hợp lệ, hệ thống yêu cầu nhập lại.
#### Lý do thiết kế:
Dựa trên phân tích, thời gian làm việc là thông tin đầu vào quan trọng để tính lương, cần được nhân viên cung cấp hoặc cập nhật chính xác.

---

## 2. Process Payroll
#### Mô tả:
Tự động tính lương cho nhân viên dựa trên thời gian làm việc, thông tin khấu trừ thuế, và các khoản phí.
#### Luồng sự kiện:
1. Tác nhân chính: Hệ thống Payroll.
2. Luồng chính:
    - Hệ thống tự động kích hoạt việc tính toán lương theo lịch định kỳ.
    - Hệ thống truy vấn thời gian làm việc từ **ProjectManagementDatabase**.
    - Hệ thống áp dụng công thức tính lương:
        - Tổng lương = Giờ làm việc * Mức lương giờ.
        - Trừ đi các khoản khấu trừ thuế, bảo hiểm.
    - Lưu kết quả tính lương vào cơ sở dữ liệu.
3. Luồng phụ:
    - Nếu dữ liệu không đầy đủ hoặc có lỗi, thông báo cho quản trị viên.
#### Lý do thiết kế:
Tự động hóa việc tính toán giúp đảm bảo hiệu quả và độ chính xác trong quản lý lương.

---

### 3. Generate Paycheck
#### Mô tả:
Tạo phiếu lương chi tiết cho nhân viên.
#### Luồng sự kiện:
1. Tác nhân chính: Hệ thống Payroll.
2. Luồng chính:
    - Hệ thống lấy dữ liệu từ quá trình **Process Payroll**.
    - Tạo phiếu lương bao gồm thông tin:
        - Tổng lương.
        - Khấu trừ thuế, bảo hiểm.
        - Số tiền nhận thực tế.
    - Lưu phiếu lương vào cơ sở dữ liệu.
3. Luồng phụ:
    - Nếu nhân viên yêu cầu, gửi phiếu lương qua email.
#### Lý do thiết kế:
Nhân viên cần phiếu lương để biết chi tiết thu nhập, khấu trừ và số tiền nhận.

---

## 4. Select Payment Method
#### Mô tả:
Nhân viên chọn phương thức nhận lương: chuyển khoản ngân hàng hoặc nhận tiền mặt.
#### Luồng sự kiện:
1. Tác nhân chính: Nhân viên.
2. Luồng chính:
    - Nhân viên chọn chức năng "Select Payment Method".
    - Nhân viên chọn phương thức nhận lương.
        - Nếu chọn chuyển khoản: Nhập thông tin tài khoản ngân hàng.
        - Nếu chọn tiền mặt: Xác nhận thông tin nhận lương tại công ty.
    - Hệ thống cập nhật thông tin thanh toán.
3. Luồng phụ:
    - Nếu tài khoản ngân hàng không hợp lệ, hệ thống yêu cầu nhập lại.
#### Lý do thiết kế:
Nhân viên có nhu cầu chọn phương thức nhận lương phù hợp với điều kiện cá nhân.

---

## 5. Generate Payroll Reports
#### Mô tả:
Tạo báo cáo tổng quan về lương, khấu trừ, và chi trả cho toàn bộ nhân viên.
#### Luồng sự kiện:
1. Tác nhân chính: Phòng kế toán.
2. Luồng chính:
    - Phòng kế toán chọn chức năng "Generate Payroll Reports".
    - Hệ thống tổng hợp dữ liệu từ các phiếu lương đã tính.
    - Báo cáo được tạo bao gồm:
        - Tổng số tiền đã chi trả.
        - Số tiền khấu trừ thuế và bảo hiểm.
        - Thống kê các khoản chi lương theo phòng ban.
    - Lưu báo cáo và gửi cho phòng kế toán.
3. Luồng phụ:
    - Nếu không đủ dữ liệu, hệ thống yêu cầu kiểm tra lại.
#### Lý do thiết kế:
Báo cáo là công cụ cần thiết để quản lý chi trả lương và hỗ trợ kiểm toán.



---

# Mô hình tổng quan Use Case





