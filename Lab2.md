# Phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
## 1. Phân tích các ca sử dụng
### Maintain Timecard
* Mô tả: Nhân viên nhập hoặc chỉnh sửa thời gian làm việc (ngày, giờ bắt đầu, giờ kết thúc) trong tuần. Thông tin này được sử dụng để tính lương.
* Tác nhân: Nhân viên.
* Diễn viên phụ: Hệ thống cơ sở dữ liệu.
* Luồng chính:
    - Nhân viên truy cập vào hệ thống và chọn "Maintain Timecard".
    - Nhân viên nhập thời gian làm việc hoặc cập nhật thời gian đã có.
    - Hệ thống lưu lại thời gian làm việc của nhân viên trong cơ sở dữ liệu.
### Process Payroll
* Mô tả: Hệ thống tự động tính toán lương dựa trên thời gian làm việc đã nhập, bao gồm khấu trừ thuế và các khoản phí khác.
* Tác nhân: Hệ thống Payroll.
* Diễn viên phụ: Hệ thống cơ sở dữ liệu.
* Luồng chính:
    - Hệ thống truy xuất thời gian làm việc của từng nhân viên.
    - Hệ thống tính lương dựa trên số giờ làm việc và các yếu tố khấu trừ.
    - Kết quả được lưu lại và có thể được gửi tới phòng kế toán.
### Generate Paycheck
* Mô tả: Dựa trên thông tin lương, hệ thống tạo phiếu lương cho nhân viên, chứa các chi tiết về lương, khấu trừ và số tiền nhận.
* Tác nhân: Hệ thống Payroll.
* Diễn viên phụ: Nhân viên.
* Luồng chính:
    - Hệ thống tổng hợp thông tin lương, khấu trừ.
    - Phiếu lương được tạo ra và lưu trữ.
    - Nhân viên có thể truy cập và xem phiếu lương.
### Select Payment Method
* Mô tả: Nhân viên chọn phương thức nhận lương, như chuyển khoản ngân hàng hoặc tiền mặt.
* DTác nhân: Nhân viên.
* Diễn viên phụ: Hệ thống Payroll.
* Luồng chính:
    - Nhân viên chọn mục "Select Payment Method".
    - Nhân viên chọn phương thức nhận lương mong muốn.
    - Hệ thống cập nhật phương thức thanh toán trong hồ sơ của nhân viên.
### Generate Payroll Reports
* Mô tả: Tạo báo cáo về lương, khấu trừ, và chi trả cho toàn bộ nhân viên.
* Tác nhân: Hệ thống Payroll.
* Diễn viên phụ: Phòng kế toán.
* Luồng chính:
    - Hệ thống thu thập thông tin lương và khấu trừ từ cơ sở dữ liệu.
    - Hệ thống tạo báo cáo tổng quan và lưu trữ.
    - Báo cáo được cung cấp cho phòng kế toán để kiểm tra.

  
