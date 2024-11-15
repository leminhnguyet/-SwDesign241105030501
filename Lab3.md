# I. Vẽ biểu đồ ngữ cảnh của các hệ thống con và giải thích:
## Biểu đồ ngữ cảnh của hệ thống con:
![Biểu đò ngữ cảnh](https://planttext.com/api/plantuml/png/V951Ri9034NtFeKlq0kmg52fs5L2S08pOy3jZ0CUfrBEraMFr2jq4eH2LDBjr_lVt_RFr_UoE9ctEG45Rmmtr5cJqguhpXbONRp35zAFgR8nKT-nVKhWKMlUEVWRAHqvL_6LdFPK662IYa_FyomkSCqUJkYIEP1598rulk8OAmNptZvuCcc1M_RMz9-qlzt6RQj_HIcqYPonK2BhXW1HSUcrVKNHZRGSsE3E-A39gj63M1xnHrSPhpfqlxHS_3Qv93dNxXKHFSA4dLzyu3dUPm0iMMF_yby0003__mC0)
## 1. Biểu đồ ngữ cảnh của BankSystem:
### Mô tả hệ thống con BankSystem:
* BankSystem chịu trách nhiệm xử lý các giao dịch thanh toán, chuyển tiền cho nhân viên trong hệ thống Payroll.
* Giao diện của hệ thống này với Payroll System là thông qua các API hoặc dịch vụ web để gửi yêu cầu chuyển tiền.
* BankSystem cũng sẽ nhận các thông tin về tài khoản nhân viên (như số tài khoản ngân hàng) và thông tin chi trả từ hệ thống Payroll.
### Interface của BankSystem:
* Chức năng:Xử lý thanh toán lương cho nhân viên.
* Giao diện:API hoặc web service để nhận và gửi yêu cầu thanh toán, kiểm tra trạng thái giao dịch.
## 2. Biểu đò ngữ cảnh của PrintService:
### Mô tả hệ thông con PrintService:
* PrintService chịu trách nhiệm in các báo cáo hoặc bảng lương cho nhân viên trong Payroll System.
* Hệ thống sẽ nhận các yêu cầu in từ Payroll System, như bảng lương hoặc báo cáo chi tiết về tiền lương, và gửi dữ liệu đến máy in.
### Interface của PrintService:
* Chức năng: In bảng lương hoặc báo cáo cho nhân viên.
* Giao diện: API hoặc dịch vụ để nhận yêu cầu in và gửi dữ liệu in.
## 3. Biểu đồ ngữ cảnh của ProjectManagementDatabase:
### Mô tả hệ thống con ProjectManagementDatabase:
* ProjectManagementDatabase lưu trữ dữ liệu về các dự án, công việc, và các thời gian làm việc của nhân viên.
* Hệ thống này có thể cung cấp thông tin về công việc, giờ làm việc của nhân viên và các dữ liệu cần thiết khác cho hệ thống Payroll để tính lương đúng.
### Interface của ProjectManagementDatabase:
* Chức năng: Cung cấp thông tin về công việc, giờ làm việc của nhân viên cho hệ thống Payroll.
* Giao diện: API hoặc giao diện kết nối CSDL để truy vấn dữ liệu công việc, giờ làm việc.

## Biểu đồ ngữ cảnh tổng quan:
## 1. Payroll System sẽ giao tiếp với:
* BankSystem: Thực hiện các giao dịch thanh toán.
* PrintService: In bảng lương hoặc báo cáo.
* ProjectManagementDatabase: Lấy dữ liệu về công việc và giờ làm việc của nhân viên.

## 2. Tác nhân:
* Payroll System: Hệ thống chính quản lý toàn bộ quy trình tính toán và xử lý lương.
* BankSystem: Thực hiện các giao dịch thanh toán.
* PrintService: Cung cấp chức năng in ấn báo cáo.
* ProjectManagementDatabase: Cung cấp thông tin về công việc và giờ làm việc.
# II. Analysis class to design element map

| Analysis Class            | Design Element                       |
|---------------------------|--------------------------------------|
| Employee                  | Employee (Entity Class)              |
| PayrollProcessor          | PayrollCalculation (Control)        |
| Timecard                  | Timecard (Entity Class)             |
| PaymentMethod             | PaymentMethodManager (Control)      |
| Payslip                   | PayslipGenerator (Boundary)         |
| ReportGenerator           | PayrollReportService (Boundary)     |

# III. 3.	Design element to owning package map

| Design Element            | Owning Package              |
|---------------------------|-----------------------------|
| Employee                  | `fa.training.entities`      |
| PayrollCalculation        | `fa.training.services`      |
| Timecard                  | `fa.training.entities`      |
| PaymentMethodManager      | `fa.training.controllers`   |
| PayslipGenerator          | `fa.training.boundaries`    |
| PayrollReportService      | `fa.training.boundaries`    |

# IV. 4.	Architectural layers and their dependencies
* Application Layer - Xử lý giao diện và điều khiển chính của ứng dụng.
* Business Services Layer - Chứa các dịch vụ nghiệp vụ cốt lõi.
* Domain Layer - Chứa các lớp đối tượng nghiệp vụ và logic xử lý.
* Infrastructure Layer - Xử lý việc truy cập cơ sở dữ liệu, tích hợp các hệ thống bên ngoài.
### biểu đồ mô tả các layers trong hệ thống và quan hệ giữa chúng;
![Biểu đồ](https://planttext.com/api/plantuml/png/VD5D2i8m40NWVKunTDyBY1HRiYa8BZp14CSIcav39XL4F9aBZ-GLR2r8gj2imalUHtvUZ-TE8eOuT4v9QzbZm0vCt_cUYUCnNXr181EH6qTAUJGjDWHPwRsp1gFj6VPufP012fHxk2aOnrU0RBjrqtfHGDB9r3t1ga4iamWSALoi8Kd8QfNyQovXtNTeqmFgLMtUlYHgFWUK60OJXq09LQzIozg771ydpulfGXlGv8bF0WTMrHphdrZFSVqJgzquctxh3G00__y30000)





