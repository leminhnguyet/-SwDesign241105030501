# 1. Phân tích kiến trúc.
## Presentation Layer
      - UI Components : gồm các thành phần tạo nên giao diện của ứng dụng (GUI). Chúng chịu trách nhiệm thu nhận và hiển thị dữ liệu cho người dùng… Ví dụ : textbox, button, combobox, …
      - UI Process Components : là thành phần chịu trách nhiệm quản lý các quá trình chuyển đổi giữa các UI… Ví dụ : Sắp xếp quá trình kiểm tra thông tin khách hàng:
        + Hiển thị màn hình tra cứu ID.
        + Hiển thị màn hình thông tin chi tiết khách hàng tương ứng
        + Hiển thị màn hình liên lạc với khách hàng.
## Bussiness Layer
      - Service Interface : là thành phần giao diện lập trình mà lớp này cung cấp cho lớp Presentation sử dụng.
      - Bussiness Workflows : chịu trách nhiệm xác định và điều phối các quy trình nghiệp vụ gồm nhiều bước và kéo dài. Những quy trình này phải được sắp xếp và thực hiện theo một thứ tự chính xác.
      Ví dụ : Thực hiện mua một đơn hàng trên tiki qua nhiều bước : kiểm tra gói hàng còn không?, tính tổng chi phí, cho phép giao dịch và sắp xếp việc giao hàng.
      - Bussiness Components : chịu trách nhiệm kiểm tra các quy tắc nghiệp vụ, ràng buộc logic và thực hiện các công việc . Các thành phần này cũng thực hiện các dịch vụ mà Service Interface cung cấp và Business Workflows sẽ sử dụng nó.
      Ví dụ : Tiếp tục ví dụ ở trên. Bạn sẽ cần một Bussiness Component để kiểm tra gói hàng có khả dụng không ? hay một component để tính tổng chi phí,…
      - Bussiness Entities : thường được sử dụng như Data Transfer Objects ( DTO ) . Bạn có thể sử dụng để truyền dữ liệu giữa các lớp (Presentation và Data Layer). Chúng thường là cấu trúc dữ liệu ( DataSets, XML,… ) hay các lớp đối tượng đã được tùy chỉnh.
      Ví dụ : tạo 1 class Student lưu trữ các dữ liệu về tên, ngày sinh, ID, lớp.
## Data Layer      
      - Data Access Logic Components : chịu trách nhiệm chính lưu trữ và truy xuất dữ liệu từ các nguồn dữ liệu (Data Sources) như XML, file system,… Hơn nữa còn tạo thuận lợi cho việc dễ cấu hình và bảo trì.
      - Service Agents: giúp bạn gọi và tương tác với các dịch vụ từ bên ngoài một cách dễ dàng và đơn giản.  
![Biểu đồ Package](https://www.planttext.com/api/plantuml/png/V99DYW8n44RtVOh2lHTm8JRgGb1eK5U3Yp9TQ30_JIeED38dcuL7yWgcjOd6LhV5gvUlFdBvFu_Oe_D7hR8AnG5t1Bt24PFnwAKrCCUQN0zE6S3FUZQsnZkh5BbDzfSzLlAgKb9qDmgiTL0joVrAGPjcj9AQ1Beopfuz4wjHfegfhfIjwRxS-XRazxPCTAcd8CUIFHb1YMo27hV8zrVJUw3V7tO2mm3MJFmMVJqaig-E6ntF25Wk1F4DxJY-i8_fSzAsYa0s0KDvNJ9Mb41lKyP-0jfso526uQUednT6PChcMrq1003__mC0)
# 2. Cơ chế Phân tích.
    Để xây dựng hệ thống Payroll System hiệu quả, cần xác định và đề xuất các cơ chế phân tích phù hợp, đảm bảo hệ thống đáp ứng đầy đủ yêu cầu nghiệp vụ. Dưới đây là danh sách các cơ chế cần giải quyết và lý do lựa chọn:

## Quản lý và lưu trữ thông tin nhân viên
    Mô tả: Cơ chế này đảm bảo lưu trữ đầy đủ thông tin cá nhân và thông tin liên quan đến lương của nhân viên, bao gồm các thuộc tính như mã nhân viên, tên, địa chỉ, phương thức thanh toán, v.v.
    Lý do: Thông tin nhân viên là dữ liệu cốt lõi của hệ thống. Quản lý và lưu trữ thông tin này giúp hệ thống truy xuất dễ dàng khi thực hiện các chức năng liên quan như tính toán lương, tra cứu hồ sơ nhân viên.

## Tính toán lương và các khoản thanh toán
    Mô tả: Cơ chế này xử lý các quy trình tính toán lương dựa trên các dữ liệu về công việc đã hoàn thành, số giờ làm, và các thông tin bổ sung (như phụ cấp, thuế).
    Lý do: Đảm bảo tính chính xác trong quy trình tính lương, tránh nhầm lẫn trong việc thanh toán và thực hiện các khoản khấu trừ cần thiết, đáp ứng yêu cầu nghiệp vụ.

## Quản lý thời gian làm việc (Timecard)
    Mô tả: Cơ chế này cho phép nhân viên hoặc bộ phận quản lý cập nhật thông tin thời gian làm việc, bao gồm ngày giờ làm việc và số giờ làm thực tế của mỗi nhân viên.
    Lý do: Đây là nền tảng cho việc tính toán lương theo giờ. Quản lý chính xác thời gian làm việc giúp hệ thống thực hiện các tính toán lương phù hợp với thời gian làm thực tế của nhân viên.

## Xác thực và phân quyền
    Mô tả: Cơ chế xác thực và phân quyền nhằm đảm bảo chỉ những người có quyền mới được phép truy cập và thực hiện các chức năng nhất định của hệ thống.
    Lý do: Đảm bảo an toàn cho dữ liệu hệ thống, tránh rủi ro khi có truy cập trái phép vào thông tin nhạy cảm của nhân viên.

## Quản lý phương thức thanh toán
    Mô tả: Cơ chế này cho phép lưu trữ và quản lý các phương thức thanh toán khác nhau của nhân viên, chẳng hạn như tiền mặt, chuyển khoản ngân hàng, hoặc séc.
    Lý do: Hệ thống cần linh hoạt trong việc xử lý các phương thức thanh toán đa dạng, đảm bảo thuận tiện cho nhân viên và bộ phận quản lý tài chính.

## Lưu trữ lịch sử và báo cáo
    Mô tả: Cơ chế này giúp lưu trữ lịch sử giao dịch lương và cung cấp các báo cáo về tình trạng thanh toán, lịch sử giờ làm, và báo cáo tổng hợp về lương cho các kỳ lương.
    Lý do: Việc lưu trữ lịch sử và báo cáo giúp quản lý dễ dàng tra cứu thông tin, đồng thời đảm bảo tuân thủ các yêu cầu về ghi nhận và báo cáo cho các mục đích nội bộ hoặc pháp lý.

# 3.Phân tích Ca Sử Dụng: Payment
    Mô tả: Ca sử dụng "Payment" cho phép nhân viên chọn phương thức thanh toán (như chuyển khoản ngân hàng, tiền mặt, séc) để nhận lương. Ca sử dụng này bao gồm các thao tác như xác định nhân viên, xử lý yêu cầu thanh toán, cập nhật phương thức thanh toán của nhân viên, và lưu trữ thông tin vào cơ sở dữ liệu.

## Các Lớp Phân Tích Chính
### UIController
    - Nhiệm vụ: Nhận yêu cầu từ người dùng, kích hoạt quy trình chọn phương thức thanh toán.
    - Quan hệ: Giao tiếp với PaymentService để xử lý yêu cầu.
### PaymentService
    - Nhiệm vụ: Xử lý logic nghiệp vụ chọn phương thức thanh toán, xác định và cập nhật phương thức thanh toán cho nhân viên.
    - Quan hệ: Tương tác với Employee và PaymentMethod để lấy thông tin và cập nhật cơ sở dữ liệu.
### Employee
    - Thuộc tính:
       id: Mã định danh duy nhất của nhân viên.
       name: Tên của nhân viên.
       address: Địa chỉ của nhân viên.
    - Nhiệm vụ: Lưu thông tin cơ bản của nhân viên và liên kết với phương thức thanh toán.
    - Quan hệ: Tương tác với PaymentMethod để lưu trữ phương thức thanh toán hiện tại.
### PaymentMethod
    - Thuộc tính:
        methodType: Loại phương thức thanh toán (VD: ngân hàng, tiền mặt).
        details: Thông tin chi tiết về phương thức thanh toán (VD: số tài khoản ngân hàng).
    - Nhiệm vụ: Lưu thông tin chi tiết về phương thức thanh toán của nhân viên.
    - Quan hệ: Liên kết với Employee.
### Database
    - Nhiệm vụ: Lưu trữ và quản lý thông tin thanh toán của nhân viên.
    - Quan hệ: Giao tiếp với PaymentService để lưu và xác nhận thay đổi.
## Biểu Đồ Sequence: Payment
![Biểu đò Sequence](https://www.planttext.com/api/plantuml/png/R94n3i8m34Ntd28Z35o00I4L1WOa9DG3cDH0f3Ik4WFgsHWu4bV04MeXRSVa__VzdRoVhtLa27ohdGB357GPCQX6hgon3NZMvQuWpu6S6mW7Q6lqVCHmjmOpQLitZbh4AVyU-KfLfco0uGGHbKhJzMAL3TLB7T6XuInWDbUPIQ2ya61D88CnzlSfn98NT60LkAiisDdwgZkAjrT-8xuLn7h1KQjnTBTUMWJkE0HwUJ6rWo5_jg66L7oKFV5ILteKVuZahz5NwNy_0000__y30000)

## Biểu Đồ Lớp: Payment
![Biểu đồ Lớp](https://www.planttext.com/api/plantuml/png/N92_3i8W48TtdkBIgGuTN1bC5qSJa_e212wLX3yDd4qQuvCv-4Y-WYssLJe1luFxlkFzVDMHHA2RDKmQ4ICSRMVyW0Xt1b21LXoqexHtmYA7Xe9sRGg4KW5Z_Ci0MgIp62mwEY5TlIft7BA0FTYCokAPPzFXCdGvII49RNwaROy6Gw_bLngW2rwENclDe2JjNRdCDYhrNYUJTTnYNq1L7TAQYt68gKDa6zXqVNdFQdHg-iKF0000__y30000)

# 4. Phân tích Ca Sử Dụng: Maintain Timecard
    Mô tả: Ca sử dụng "Maintain Timecard" cho phép nhân viên cập nhật thời gian làm việc của họ thông qua việc ghi nhận giờ vào và giờ ra. Điều này bao gồm việc nhập thông tin thời gian, xác minh dữ liệu, và lưu trữ các thông tin này vào cơ sở dữ liệu.

## Các Lớp Phân Tích Chính
### UIController
    - Nhiệm vụ: Nhận thông tin từ người dùng về thời gian làm việc và kích hoạt quy trình cập nhật timecard.
    - Quan hệ: Giao tiếp với TimecardService để xử lý yêu cầu cập nhật.
### TimecardService
    - Nhiệm vụ: Xử lý logic nghiệp vụ cho việc cập nhật timecard, xác minh tính hợp lệ của dữ liệu đầu vào.
    - Quan hệ: Tương tác với Employee và Timecard để lấy và lưu thông tin.
### Employee
    - Thuộc tính:
         id: Mã định danh duy nhất của nhân viên.
         name: Tên của nhân viên.
    - Nhiệm vụ: Lưu thông tin về nhân viên và liên kết với timecard.
    - Quan hệ: Tương tác với Timecard để cập nhật thông tin thời gian.
### Timecard
    - Thuộc tính:
         date: Ngày làm việc.
         hoursWorked: Số giờ làm việc trong ngày.
    - Nhiệm vụ: Lưu trữ thông tin về thời gian làm việc của nhân viên.
    - Quan hệ: Liên kết với Employee.
### Database
    - Nhiệm vụ: Lưu trữ và quản lý thông tin thời gian làm việc của nhân viên.
    - Quan hệ: Giao tiếp với TimecardService để lưu và xác nhận thay đổi.
## Biểu Đồ Sequence: Maintain Timecard
![Biểu đò Sequence](https://www.planttext.com/api/plantuml/png/T94n3i8m34Ntd28Z35o00I4L99YXOZQf4H5j73akYBCnS2IkW3kqQaiPu__Vzq_oURtNIO2bhae3JeXjdf1Dr95tFa8Gc-yp2i9KbYFXw2jqmCK1-UuT3hHj5Kjw8au2W-461CwGq9Xcirsi1Wljqc8Gv1QTpSr0LlkeXXAHoM5AFMRiKQnjgFwB3qLxL7EdzCBLLSS217TKSpeHt_1FRdiV9HBSiLUYKnQJhHs5Y-SAn5Fu3VvzbtIbHzPZTCCQGz7yv1S00F__0m00)
## Biểu đò Lớp: Maintain Timecard
![Biểu đồ Lớp](https://www.planttext.com/api/plantuml/png/R50x3i8m3DrpYgTEWEZ0cW5rW1E0n1mb5aGqIPMabH3YP0mSYIkGbgP8m63Bl-VtxEVzKOKeV6nDpMGjGi3MDBMx4E7AW19QSMWRXzWAGnoxwBKzfWBGDaf4scj3KdWroy6SetDQiHiRT-R6kBC7SMoI7zAJQtquE7-caUi7joFVQVcM13JUIGfXeisAb_WZO3gdM1KeopMAHV7Hms54OamMs3TPFvpHh2Ah-X-z0000__y30000)


# 5. Hợp Nhất Kết Quả Phân Tích
## Ca Sử Dụng Payment
    Nhiệm vụ: Cho phép nhân viên chọn và cập nhật phương thức thanh toán cho lương.
    Lớp Phân Tích:
        UIController: Nhận yêu cầu từ người dùng.
        PaymentService: Xử lý logic chọn phương thức thanh toán.
        Employee: Lưu trữ thông tin nhân viên.
        PaymentMethod: Lưu trữ thông tin phương thức thanh toán.
        Database: Lưu trữ và quản lý thông tin thanh toán.
    Biểu Đồ Sequence: Hiển thị quy trình xử lý yêu cầu chọn phương thức thanh toán.
    Biểu Đồ Lớp: Mô tả mối quan hệ giữa các lớp trong ca sử dụng Payment.

## Ca Sử Dụng Maintain Timecard
    Nhiệm vụ: Cho phép nhân viên cập nhật thời gian làm việc của họ.
    Lớp Phân Tích:
        UIController: Nhận thông tin từ người dùng.
        TimecardService: Xử lý logic cập nhật timecard.
        Employee: Lưu trữ thông tin nhân viên.
        Timecard: Lưu trữ thông tin thời gian làm việc.
        Database: Lưu trữ và quản lý thông tin thời gian làm việc.
    Biểu Đồ Sequence: Hiển thị quy trình xử lý yêu cầu cập nhật thời gian làm việc.
    Biểu Đồ Lớp: Mô tả mối quan hệ giữa các lớp trong ca sử dụng Maintain Timecard.


