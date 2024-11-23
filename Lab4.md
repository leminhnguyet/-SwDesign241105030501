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
1. Quản trị viên đăng nhập vào hệ thống.
2. Quản trị viên chọn mục "Manage Employee Information" trong menu quản lý.
3. Hệ thống hiển thị danh sách thông tin nhân viên hiện có.
4. Quản trị viên chọn thêm, sửa hoặc xóa thông tin nhân viên.
5. Nếu thêm nhân viên mới, hệ thống yêu cầu nhập các thông tin cần thiết và xác nhận.
6. Nếu sửa, hệ thống hiển thị thông tin của nhân viên để chỉnh sửa.
7. Nếu xóa, hệ thống yêu cầu xác nhận việc xóa nhân viên khỏi hệ thống.
8. Sau khi thực hiện thao tác, hệ thống cập nhật dữ liệu và thông báo kết quả thành công hoặc thất bại.

### Luồng thay thế:
- Nếu nhập thông tin không hợp lệ (ví dụ: định dạng số điện thoại sai), hệ thống sẽ yêu cầu nhập lại.
- - Nếu nhân viên không tồn tại trong cơ sở dữ liệu khi sửa hoặc xóa, hệ thống sẽ thông báo lỗi.

### Lý do thiết kế:
- Việc quản lý thông tin nhân viên là một phần quan trọng của hệ thống Payroll System, giúp đảm bảo tính chính xác trong quá trình tính toán và trả lương. Bằng cách cho phép quản trị viên dễ dàng cập nhật, sửa đổi hoặc xóa thông tin, hệ thống sẽ luôn duy trì cơ sở dữ liệu nhân viên chính xác và đầy đủ.

### PlantUML Use Case:
![Biểu đồ](https://www.planttext.com/api/plantuml/png/n9CzJWCn48Lxds9AAABq52WHIK5BJZ3iJC2IVu8zteYpKN0ahe3jRAALjLcemCKKtldclRUslpu-Lr4mIB96OIS-m9giTgfMMDp3rXwCVsVUSUXrntVmn6-9eu1uiEZmXO675Y0KL0rGPcpo_ZF62alGt8yOxVPUdHjWCQqeARX6vhh1DT5oIrgM6pOihHGQAHtW-7ZveY2lMTyxp9x7oCb4uUQzFtYtry6YQE-cPJ9LisIHLt-4cBgEOmIRI_cvDsS0a8ZfLh79MYNVX9UVCwH3RcRwpno3XI59UqY_otAL-hCKL1sK58xgfNfqFHfDCm6QsHn2VcwNoMF-D7MLItcNtm000F__0m00)

---

## 2. Maintain Timecard

### Mô tả:
- Ca sử dụng này cho phép nhân viên nhập thời gian làm việc và quản trị viên theo dõi các giờ làm việc của nhân viên.
- Hệ thống lưu trữ dữ liệu về giờ làm việc của nhân viên để tính toán lương chính xác.

### Tác nhân:
- **Employee**: Nhập thời gian làm việc hàng ngày.
- **Admin**: Quản lý và xem lại giờ làm việc của nhân viên.

### Luồng chính:
1. Nhân viên đăng nhập vào hệ thống và chọn mục "Manage Timecard".
2. Hệ thống hiển thị danh sách các thẻ công hiện tại của nhân viên.
3. Nhân viên chọn ngày hoặc khoảng thời gian muốn chỉnh sửa.
4. Nhân viên nhập hoặc chỉnh sửa giờ vào, giờ ra, và số giờ làm việc.
5. Hệ thống tính toán tổng số giờ làm việc dựa trên thông tin đã nhập.
6. Nhân viên lưu thông tin thẻ công.
7. Hệ thống lưu và cập nhật thẻ công của nhân viên vào cơ sở dữ liệu.

### Luồng thay thế:
- Nếu thông tin giờ làm việc không hợp lệ (ví dụ: chồng lấn giờ, thiếu thông tin), hệ thống sẽ thông báo lỗi và yêu cầu nhân viên nhập lại.
- Nếu nhân viên không có quyền chỉnh sửa thẻ công của mình (trong trường hợp là Admin), hệ thống sẽ yêu cầu Admin thực hiện thao tác này.
- Nếu có lỗi kết nối với cơ sở dữ liệu khi lưu thẻ công, hệ thống sẽ thông báo lỗi và yêu cầu thử lại sau.

### Lý do thiết kế:
- Việc quản lý thẻ công là cần thiết để tính toán chính xác số giờ làm việc của nhân viên và từ đó tính lương cho họ. Ca sử dụng này giúp đảm bảo nhân viên có thể dễ dàng cập nhật và theo dõi thời gian làm việc của mình, đồng thời quản trị viên có thể kiểm tra và chỉnh sửa khi cần thiết.
  
### PlantUML :
![Biểu đồ](https://www.planttext.com/api/plantuml/png/h5DBJiCm4Dtx5BCaYrw01Me5BDXIBZ34KseHs-budAXdOy6Hk0AJA8vGWL8eNbYQyRoFzUotbzTb4cJ9lZ5OIsIuzMqJzqHJkRBU1LEQiBY21-UfHhPhuixLT0dtjCkK12H2vwW7HP5rMa-3vW0naDoWu2Ec4ItigADv7AoUcJ80Ywyb9NCuW1mrUHVQBBErFl8pR6FcTDpS6dzfx3g6ZMEFucBuJAs8ObAvjx67bEkQKWAl6puHN1GC99MsbS56r7k7ZPlqGTS9nCIibvrfFr9KXe8rOx1_oXCsGwSyazF2BUFdf_ozxpCYpgroa_tVg4UdF-OyILTcgQaCt_0T003__mC0)

---

## 3. Process Payroll

### Mô tả:
- Ca sử dụng này cho phép hệ thống tính toán và xử lý lương cho nhân viên dựa trên các yếu tố như số giờ làm việc, mức lương cơ bản, các khoản phụ cấp, và các khoản khấu trừ. Sau khi lương được tính toán, hệ thống sẽ thực hiện các giao dịch thanh toán cho nhân viên.

### Tác nhân:
- **Admin**: Quản trị viên, người có thể khởi tạo và quản lý quá trình xử lý lương.
- **BankSystem**: Hệ thống ngân hàng, thực hiện các giao dịch thanh toán lương cho nhân viên.
- **PrintService**: Hệ thống in ấn, in bảng lương cho nhân viên.
- **ProjectManagementDatabase**: Cung cấp thông tin về giờ làm việc của nhân viên để tính lương.

### Luồng chính:
1. Quản trị viên đăng nhập vào hệ thống và chọn "Process Payroll".
2. Hệ thống lấy thông tin về giờ làm việc của nhân viên từ ProjectManagementDatabase.
3. Hệ thống tính toán lương dựa trên số giờ làm việc, mức lương cơ bản, phụ cấp và khấu trừ.
4. Hệ thống tạo bảng lương cho tất cả nhân viên và lưu trữ bảng lương trong cơ sở dữ liệu.
5. Hệ thống gửi yêu cầu thanh toán cho BankSystem để thực hiện các giao dịch chuyển tiền cho nhân viên.
6. BankSystem thực hiện thanh toán và phản hồi kết quả cho hệ thống.
7. Hệ thống gửi yêu cầu in bảng lương cho PrintService.
8. PrintService in bảng lương cho nhân viên và gửi lại kết quả cho hệ thống.
9. Hệ thống hoàn tất và thông báo đã hoàn thành quá trình xử lý lương.

### Luồng thay thế:
- Nếu hệ thống không thể kết nối với ProjectManagementDatabase để lấy thông tin giờ làm việc, hệ thống sẽ thông báo lỗi và yêu cầu thử lại.
- Nếu có lỗi trong quá trình thanh toán qua BankSystem, hệ thống sẽ thông báo lỗi và yêu cầu thử lại sau.
- Nếu có lỗi trong quá trình in bảng lương qua PrintService, hệ thống sẽ thông báo lỗi và yêu cầu thử lại.

### Lý do thiết kế:
- Xử lý lương là một phần quan trọng trong hệ thống Payroll, giúp đảm bảo nhân viên nhận được mức lương chính xác theo công việc đã làm. Quá trình xử lý lương bao gồm việc tính toán chính xác số giờ làm việc và các yếu tố khác, sau đó thực hiện thanh toán và in bảng lương cho nhân viên. Hệ thống cần đảm bảo các bước này được thực hiện tự động và chính xác để tiết kiệm thời gian và giảm sai sót.

### PlantUML Use Case:
![Biểu đồ](https://www.planttext.com/api/plantuml/png/d5HBRi8m4Dtx5BDi5ro0HKKBNNHH2PKJJEC1N1mxs1DGpjP5ZzGhTF9hI4aQYInGyCnxR_pcAT-VNul863XFhSA4VO17dHhNl3-XEsoAo9Gs1-jW76yed4n2lqV-Wn9-HOSxIidn2XdVCP9I5HNC7c2DHV3MIcj2CHgtcyEBCsoG2RAw1bbTL5Uz5S6Oo1pUY8EX4m6bcVK54PnzEC3Uvq78nd0m6nvBsFBWBYX02s9agFfmYJR9BRBnRWxj7uA85aEXhficf6iSQ68qTiIExlORF5KMHckogAPkj_HkQq9QZJ7Ct6sylwBIE-20BihM1HrLrpccjcvWoQJgPQnA8uuvHMwl9ScGgdIgoxP_H3iGwI4z0LR95FVs_lmtWAJx0okq3CyXIDHr7ae2tRgCIPLOa6TQXYgALAeIHRXRzKbWAzicVQ_8wG79PWEtIRLxc91eNRvDeq7tH1RoKtvOVW000F__0m00)

---

## 4. Print Payslip and Reports

### Mô tả:
- Ca sử dụng này cho phép hệ thống in bảng lương và các báo cáo liên quan đến lương cho nhân viên. Hệ thống gửi yêu cầu in bảng lương cho từng nhân viên và các báo cáo tài chính hoặc báo cáo tổng hợp về lương cho quản trị viên.

### Tác nhân:
- **Admin**: Quản trị viên, người yêu cầu in bảng lương hoặc báo cáo.
- **PrintService**: Hệ thống in ấn, thực hiện việc in bảng lương và báo cáo.

### Luồng chính:
1. Quản trị viên đăng nhập vào hệ thống và chọn "Print Payslips and Reports".
2. Hệ thống yêu cầu quản trị viên lựa chọn giữa việc in bảng lương cho nhân viên hoặc in báo cáo tài chính.
3. Quản trị viên chọn bảng lương hoặc báo cáo và cung cấp các tham số như khoảng thời gian, tên báo cáo, vv.
4. Hệ thống lấy dữ liệu cần thiết từ cơ sở dữ liệu và gửi yêu cầu in cho PrintService.
5. PrintService tiến hành in bảng lương hoặc báo cáo theo yêu cầu.
6. Hệ thống thông báo cho quản trị viên khi việc in ấn đã hoàn thành.

### Luồng thay thế:
- Nếu có lỗi khi lấy dữ liệu từ cơ sở dữ liệu (ví dụ: không tìm thấy bảng lương hoặc báo cáo), hệ thống sẽ thông báo lỗi và yêu cầu thử lại.
- Nếu có lỗi trong quá trình in ấn, hệ thống sẽ thông báo lỗi và yêu cầu thử lại.

### Lý do thiết kế:
- In bảng lương và báo cáo tài chính giúp cung cấp thông tin chi tiết về mức lương của nhân viên, đồng thời giúp quản trị viên và các bên liên quan theo dõi và kiểm tra các khoản thanh toán. Quá trình này cần được thực hiện chính xác và hiệu quả để đảm bảo tính minh bạch trong việc chi trả lương và báo cáo tài chính.

### PlantUML Use Case:
![Biểu đồ](https://www.planttext.com/api/plantuml/png/f59BQiCm5Dph56-PGD83U55YIBV5n2TujPvJKLbIdvvTShOkUgHUeV8dYGkD2LGB8JHlPZI3lZ-_Tb6GfMsimaeyGwuRuwPpmSP9IToPYfGQ4DW-ZjS5dg8r8UPE7oXubfX1IPOgWT3Z4AO1I48yJgWRp5vqKCyWZszG9qP0neQ4EC8g41klDvCAk0HiWAHwMD_nfe9zPpJD19TUiKV15uoKmO643NLqpd6D0JeDgVCaR9VSaqhBRcGisCwBxadlBSMfH-EEQWul-nKJ1IhV19lYwjksrzAVlPZwTF6RaHLQWIVc55wtt6Dzb5J4K0vQ1MdTuL2--W-WGQUX6F58iDh_Ke8QZIMzLkJ-ihrqyG_3IpbpgrtQ-j__0m00__y30000)

---

## 5. Manage Payment Methods

### Mô tả:
- Ca sử dụng này cho phép quản trị viên quản lý các phương thức thanh toán cho nhân viên, bao gồm việc thêm, sửa, xóa các phương thức thanh toán như chuyển khoản ngân hàng, trả lương bằng tiền mặt hoặc các phương thức khác. Hệ thống sẽ cập nhật các phương thức thanh toán cho nhân viên theo yêu cầu của quản trị viên.

### Tác nhân:
- **Admin**: Quản lý các phương thức thanh toán cho nhân viên.
- **Payroll System**: Hệ thống quản lý lương, nhận thông tin phương thức thanh toán từ quản trị viên.

### Luồng chính:
1. QQuản trị viên đăng nhập vào hệ thống và chọn "Manage Payment Methods".
2. Quản trị viên có thể chọn thêm, sửa hoặc xóa một phương thức thanh toán.
3. Nếu chọn thêm phương thức thanh toán, hệ thống yêu cầu quản trị viên cung cấp các thông tin cần thiết như tên phương thức thanh toán (ví dụ: ngân hàng, tiền mặt, ...).
4. Nếu chọn sửa phương thức thanh toán, hệ thống hiển thị các thông tin phương thức thanh toán hiện tại và cho phép chỉnh sửa.
5. Nếu chọn xóa phương thức thanh toán, hệ thống yêu cầu xác nhận việc xóa.
6. Hệ thống cập nhật phương thức thanh toán vào cơ sở dữ liệu.
7.Quản trị viên nhận thông báo thành công về việc thay đổi phương thức thanh toán.

### Luồng thay thế:
- Nếu phương thức thanh toán không hợp lệ (ví dụ: số tài khoản ngân hàng sai hoặc thông tin không đầy đủ), hệ thống sẽ thông báo lỗi và yêu cầu quản trị viên chỉnh sửa lại thông tin.
- Nếu có lỗi trong quá trình cập nhật cơ sở dữ liệu (ví dụ: không kết nối được với cơ sở dữ liệu), hệ thống sẽ thông báo lỗi và yêu cầu thử lại.

### Lý do thiết kế:
- Quản lý phương thức thanh toán là một phần quan trọng trong việc xử lý lương cho nhân viên. Phương thức thanh toán có thể thay đổi theo thời gian, do đó việc cho phép quản trị viên cập nhật và duy trì thông tin này giúp hệ thống đảm bảo tính chính xác và sự linh hoạt trong việc chi trả lương cho nhân viên.

### PlantUML Use Case:
![Biểu đồ](https://www.planttext.com/api/plantuml/png/d9H1Ri8m44NtFiKiGG8EmA825HPTKA6Y7c2m9s3LiLDxGfMpTT4ZzGfrx51K2g9D5b4K-x__Ppp9v_l7B31whaiZKBBpC5Ubjjtp6XllZDaqWQaK8Yt1-0vMQ757SRKaoolYlLDX2Xio91bSnTfP6CoL6i5IQHx18gumGPK5K2R5KA3XQAUW0q4c2OZN9OVMEKMOmXEzrXJuZ0YA6BK9YN0ZxDgxWrRdcOu46D1aDnd15kqBe9Ikjh4CYM4_56HLIjwMrYFwGeVAO0EozhvLzYzXvPGkcck0Oyokz_rxB9qjj2yndIgxQD02_nBmFYkp8gfJfckkFsPj2i-LmbyZ0z4jliOj1X8_132-cQ9En2l-fx8V7RTTpRiXr59I24LjHEhcWpsWqVyOsHDuitTlGDx7xwgCoBWN1aVSvJFCivPFiQiQbYsWjzytfYklY3QaiiyitjhVm1S0003__mC0)

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
![Biểu đồ](https://www.planttext.com/api/plantuml/png/Z90n3i8m34NtdC8ZIFG23AW334XiYEvkubQHaXGvIH5dO-18N047A0AnuC63_T_tbs-NQnqJSihUATHfO3X4ObKQL2lO3RqDU-BHQbh2FhVU9d1b29h9K4WMNOHP5dr0JmiuOeodWSrSVRB5Quq9MupYqn3RxWmJ11ZCcrEJ3AgV-uzKHlOANO86dJNFC0galky9NEGbjDOKOvVTIqjEpBTX_0_VCCjJl3XWJug2KRKqUTST003__mC0)

---

