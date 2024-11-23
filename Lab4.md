# I. Thiết kế các ca sử dụng cho hệ thống Payroll System
---
## 1.Manage Employee Information

### Mô tả:
- Ca sử dụng này giúp quản trị viên (Admin) có thể thêm mới, chỉnh sửa, hoặc xóa thông tin của nhân viên trong hệ thống.
- Nhân viên có thể xem và cập nhật thông tin cá nhân của mình (nếu có quyền truy cập).

### Tác nhân:
- **Admin**: Quản lý thông tin nhân viên.
- **Employee**: Xem và cập nhật thông tin cá nhân (nếu có quyền).

### Luồng chính:
1. Tác nhân đăng nhập vào hệ thống.
2. Tác nhân chọn "Manage Employee Information".
3. Tác nhân tìm kiếm hoặc chọn nhân viên cần cập nhật thông tin.
4. Tác nhân chỉnh sửa thông tin nhân viên hoặc thêm mới nhân viên.
5. Hệ thống cập nhật dữ liệu vào cơ sở dữ liệu.

### Luồng thay thế:
- Nếu nhập thông tin không hợp lệ (ví dụ: định dạng số điện thoại sai), hệ thống sẽ yêu cầu nhập lại.

### Lý do thiết kế:
- Việc quản lý thông tin nhân viên là cơ sở quan trọng để tính toán lương và thực hiện các chức năng khác của hệ thống. Điều này đảm bảo tính chính xác của các thông tin cần thiết.

### PlantUML Use Case:
![Use Case](https://www.planttext.com/api/plantuml/png/J8-n2i9038RtF4MulHHN1wc8WuDOaBg7DfR2NQxSfPH3V3877ybNq6efRY7vllydhyUpY4f11sU1QlK1juthP9xthhS-CGC4hfMajOocf1IyjNXEKTaPl07Y4Bcc-3aUIQZbHSI3N7rmf9qNWnInsgtW3l0jmIpRJ0jSewdwXfJpMPyi0ql87tVfUCn_C9v6cSc2fPa-U0C00F__0m00)

---

## 2. Maintain Timecard

### Mô tả:
- Ca sử dụng này cho phép nhân viên nhập thời gian làm việc và quản trị viên theo dõi các giờ làm việc của nhân viên.
- Hệ thống lưu trữ dữ liệu về giờ làm việc của nhân viên để tính toán lương chính xác.

### Tác nhân:
- **Employee**: Nhập thời gian làm việc hàng ngày.
- **Admin**: Quản lý và xem lại giờ làm việc của nhân viên.

### Luồng chính:
1. Nhân viên đăng nhập vào hệ thống.
2. Nhân viên chọn "Maintain Timecard".
3. Nhân viên nhập giờ bắt đầu, giờ kết thúc, và thời gian nghỉ.
4. Hệ thống kiểm tra tính hợp lệ và lưu trữ thời gian làm việc vào cơ sở dữ liệu.
5. Admin có thể truy xuất và chỉnh sửa giờ làm việc của nhân viên nếu cần.

### Luồng thay thế:
- Nếu thông tin giờ làm việc không hợp lệ (ví dụ: chồng lấn giờ, thiếu thông tin), hệ thống sẽ thông báo lỗi và yêu cầu nhân viên nhập lại.

### Lý do thiết kế:
- Quản lý thời gian làm việc là rất quan trọng trong việc tính toán chính xác lương. Cung cấp khả năng kiểm tra và chỉnh sửa cho admin giúp hệ thống linh hoạt và dễ dàng kiểm tra tính chính xác của các dữ liệu.

### PlantUML Use Case:
![Use Case](https://www.planttext.com/api/plantuml/png/J8uz2i9048NxESLZ-pIM5XAHT0O4um66P5WMzaTs9qKGJsRXaRo2IL2ncE9zxsDcNezdNPIpZi4Jzveocd3rQHBvnFqGN2JAqYj7wmNcn5DEtkCy5PLWS2DWBD9pcSkMNTHvqBamepmOSC7biA4xqNSrgcgtC6nXcgYILnl7P0sjz_w5bYDR-Hd5K2rnMFvz0m00__y30000)

---

## 3. Process Payroll

### Mô tả:
- Ca sử dụng này cho phép quản trị viên xử lý bảng lương cho tất cả nhân viên dựa trên thời gian làm việc đã nhập và các yếu tố khác như phụ cấp, thuế, bảo hiểm.

### Tác nhân:
- **Admin**: Quản trị viên sẽ khởi động quá trình tính lương cho tất cả nhân viên.
- **Employee**: Nhân viên nhận phiếu lương.

### Luồng chính:
1. Quản trị viên đăng nhập vào hệ thống và chọn "Process Payroll".
2. Hệ thống lấy dữ liệu về thời gian làm việc từ **Maintain Timecard**.
3. Hệ thống áp dụng các quy tắc tính lương, bao gồm thuế và các phụ cấp.
4. Hệ thống tạo ra bảng lương cho tất cả nhân viên và lưu trữ kết quả vào cơ sở dữ liệu.

### Luồng thay thế:
- Nếu có lỗi trong quá trình tính toán (thiếu thông tin, sai dữ liệu), hệ thống sẽ thông báo lỗi và yêu cầu chỉnh sửa thông tin.

### Lý do thiết kế:
- Xử lý bảng lương là bước quan trọng trong hệ thống Payroll System, vì nó đảm bảo tính chính xác và minh bạch trong việc chi trả lương cho nhân viên.

### PlantUML Use Case:
![Use Case](https://www.planttext.com/api/plantuml/png/F8qn2W9134NxdE8p_LPs5hAo5n340uJP849c1f9CiOWdizWZUGLT4Tlt7_-zdklemHQzA76EPZZEvLQ9J79mlQeWdNYnfehpuY4buKv0TydissWjYpj-KW8xBjEE7aJV9mp3OGFO8qsikIk7_6qQfSwVzXi00F__0m00)

---

## 4. Print Payslip and Reports

### Mô tả:
- Ca sử dụng này cho phép quản trị viên và nhân viên xem và in bảng lương hoặc các báo cáo khác liên quan đến tiền lương.

### Tác nhân:
- **Admin**: In báo cáo bảng lương cho tất cả nhân viên.
- **Employee**: Xem và in bảng lương của chính mình.

### Luồng chính:
1. Quản trị viên hoặc nhân viên đăng nhập vào hệ thống.
2. Tác nhân chọn "Print Payslip and Reports".
3. Tác nhân chọn thời gian hoặc nhân viên cần in bảng lương.
4. Hệ thống tạo báo cáo và gửi đến máy in hoặc hiển thị dưới dạng PDF.

### Luồng thay thế:
- Nếu hệ thống không thể tạo báo cáo, sẽ có thông báo lỗi và yêu cầu thử lại.

### Lý do thiết kế:
- In bảng lương và báo cáo là tính năng cần thiết để cung cấp thông tin về lương cho nhân viên, đồng thời giúp admin theo dõi và lưu trữ các báo cáo tài chính của công ty.

### PlantUML Use Case:
![Use Case](https://www.planttext.com/api/plantuml/png/P8uz2i9048NxESLZ-tHM5f8WrehY0OPaaC3-X9q98OWdi_18Ni54tCfkUFFD--RzVDLgd6qCdhYrbD5qeO-_-H06dsOHeYojSRnvWJlnd9FtkCng4Xpk18mgBUkwp7qqB8ZwVW373cSPKZPrOCLrlw47qLU1gjgj0RRbgbbA2qr5_OyTfrW4Zcg9tVBx1m00__y30000)

---

## 5. Manage Payment Methods

### Mô tả:
- Ca sử dụng này cho phép quản trị viên quản lý các phương thức thanh toán cho nhân viên, như chuyển khoản ngân hàng hoặc trả lương bằng tiền mặt.

### Tác nhân:
- **Admin**: Quản lý các phương thức thanh toán cho nhân viên.

### Luồng chính:
1. Quản trị viên đăng nhập vào hệ thống và chọn "Manage Payment Methods".
2. Quản trị viên thêm, sửa hoặc xóa phương thức thanh toán của nhân viên.
3. Hệ thống cập nhật phương thức thanh toán cho nhân viên.

### Luồng thay thế:
- Nếu phương thức thanh toán không hợp lệ (ví dụ: số tài khoản sai), hệ thống sẽ thông báo lỗi.

### Lý do thiết kế:
- Quản lý phương thức thanh toán giúp đảm bảo quá trình chi trả lương cho nhân viên diễn ra suôn sẻ và chính xác.

### PlantUML Use Case:
![Use Case](https://www.planttext.com/api/plantuml/png/P8uz2W8n58JxTueX_M9bOo6xM0S4yG2FvBakv0UIjqLOF9c5H_8AHblRcMy-vlryZLMvw1e3iTDSCFcu9A8YJZdDGM3Et4eE0PTMLQB1Hi1QnN7jfUN4iw0pKPB2YjwphmPSSJtjwK7q4s8OZjy01vZ9-vtDVhcrlncDadp_yW400F__0m00)

---
## 6. Login

### Mô tả:
- Ca sử dụng này cho phép người dùng đăng nhập vào hệ thống để truy cập các tính năng của Payroll System.

### Tác nhân:
- **Employee**: Nhân viên cần đăng nhập vào hệ thống để xem thông tin cá nhân hoặc tham gia các tác vụ khác.
- **Admin**: Quản trị viên cần đăng nhập để quản lý hệ thống.

### Luồng chính:
1. Người dùng nhập thông tin đăng nhập (tên người dùng và mật khẩu) vào hệ thống.
2. Hệ thống xác thực thông tin đăng nhập với cơ sở dữ liệu.
3. Nếu thông tin đúng, người dùng sẽ được chuyển tới trang chính của hệ thống.
4. Nếu thông tin sai, hệ thống hiển thị thông báo lỗi yêu cầu nhập lại thông tin.

### Luồng thay thế:
- Nếu người dùng nhập sai thông tin đăng nhập (ví dụ: mật khẩu sai), hệ thống sẽ yêu cầu nhập lại.
- Nếu người dùng chưa đăng ký tài khoản, hệ thống sẽ cung cấp tùy chọn "Đăng ký".

### Lý do thiết kế:
- Đăng nhập là bước đầu tiên và quan trọng để bảo mật hệ thống. Nó giúp xác thực người dùng và đảm bảo rằng chỉ những người có quyền mới có thể truy cập vào các tính năng của hệ thống.

### Planttext UML:
![](https://www.planttext.com/api/plantuml/png/Z90n3i8m34NtdC8ZIFG23AW334XiYEvkubQHaXGvIH5dO-18N047A0AnuC63_T_tbs-NQnqJSihUATHfO3X4ObKQL2lO3RqDU-BHQbh2FhVU9d1b29h9K4WMNOHP5dr0JmiuOeodWSrSVRB5Quq9MupYqn3RxWmJ11ZCcrEJ3AgV-uzKHlOANO86dJNFC0galky9NEGbjDOKOvVTIqjEpBTX_0_VCCjJl3XWJug2KRKqUTST003__mC0)

---

