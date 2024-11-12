# Phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
## 1. Phân tích các ca sử dụng
### Maintain Timecard
* Mô tả: Nhân viên nhập hoặc chỉnh sửa thời gian làm việc (ngày, giờ bắt đầu, giờ kết thúc) trong tuần. Thông tin này được sử dụng để tính lương.
* Tác nhân: Nhân viên.
* Luồng chính:
    - Nhân viên truy cập vào hệ thống và chọn "Maintain Timecard".
    - Nhân viên nhập thời gian làm việc hoặc cập nhật thời gian đã có.
    - Hệ thống lưu lại thời gian làm việc của nhân viên trong cơ sở dữ liệu.
### Process Payroll
* Mô tả: Hệ thống tự động tính toán lương dựa trên thời gian làm việc đã nhập, bao gồm khấu trừ thuế và các khoản phí khác.
* Tác nhân: Hệ thống Payroll.
* Luồng chính:
    - Hệ thống truy xuất thời gian làm việc của từng nhân viên.
    - Hệ thống tính lương dựa trên số giờ làm việc và các yếu tố khấu trừ.
    - Kết quả được lưu lại và có thể được gửi tới phòng kế toán.
### Generate Paycheck
* Mô tả: Dựa trên thông tin lương, hệ thống tạo phiếu lương cho nhân viên, chứa các chi tiết về lương, khấu trừ và số tiền nhận.
* Tác nhân: Hệ thống Payroll.
* Luồng chính:
    - Hệ thống tổng hợp thông tin lương, khấu trừ.
    - Phiếu lương được tạo ra và lưu trữ.
    - Nhân viên có thể truy cập và xem phiếu lương.
### Select Payment Method
* Mô tả: Nhân viên chọn phương thức nhận lương, như chuyển khoản ngân hàng hoặc tiền mặt.
* DTác nhân: Nhân viên.
* Luồng chính:
    - Nhân viên chọn mục "Select Payment Method".
    - Nhân viên chọn phương thức nhận lương mong muốn.
    - Hệ thống cập nhật phương thức thanh toán trong hồ sơ của nhân viên.
### Generate Payroll Reports
* Mô tả: Tạo báo cáo về lương, khấu trừ, và chi trả cho toàn bộ nhân viên.
* Tác nhân: Hệ thống Payroll.
* Luồng chính:
    - Hệ thống thu thập thông tin lương và khấu trừ từ cơ sở dữ liệu.
    - Hệ thống tạo báo cáo tổng quan và lưu trữ.
    - Báo cáo được cung cấp cho phòng kế toán để kiểm tra.

## 2. Lab2 - PayrollSystem Project
### Timecard.java
```java
package com.payrollsystem;

import java.time.LocalDateTime;

public class Timecard {
    private int employeeId;
    private LocalDateTime clockInTime;
    private LocalDateTime clockOutTime;
    
    public Timecard(int employeeId, LocalDateTime clockInTime) {
        this.employeeId = employeeId;
        this.clockInTime = clockInTime;
    }

    public int getEmployeeId() {
        return employeeId;
    }

    public LocalDateTime getClockInTime() {
        return clockInTime;
    }

    public LocalDateTime getClockOutTime() {
        return clockOutTime;
    }

    public void clockOut(LocalDateTime clockOutTime) {
        this.clockOutTime = clockOutTime;
    }

    public long getTotalHoursWorked() {
        if (clockOutTime != null) {
            return java.time.Duration.between(clockInTime, clockOutTime).toHours();
        }
        return 0;
    }
}
```

### TimecardManager.java:
```java
package com.payrollsystem;

import java.time.LocalDateTime;
import java.util.ArrayList;
import java.util.List;

public class TimecardManager {
    private List<Timecard> timecards;

    public TimecardManager() {
        this.timecards = new ArrayList<>();
    }

    public void clockIn(int employeeId, LocalDateTime clockInTime) {
        Timecard timecard = new Timecard(employeeId, clockInTime);
        timecards.add(timecard);
        System.out.println("Employee " + employeeId + " clocked in at " + clockInTime);
    }

    public void clockOut(int employeeId, LocalDateTime clockOutTime) {
        for (Timecard timecard : timecards) {
            if (timecard.getEmployeeId() == employeeId && timecard.getClockOutTime() == null) {
                timecard.clockOut(clockOutTime);
                System.out.println("Employee " + employeeId + " clocked out at " + clockOutTime);
                break;
            }
        }
    }

    public void printTimecards() {
        for (Timecard timecard : timecards) {
            System.out.println("Employee " + timecard.getEmployeeId() + ": Clock In: " + timecard.getClockInTime() + ", Clock Out: " + timecard.getClockOutTime() + ", Hours Worked: " + timecard.getTotalHoursWorked());
        }
    }
}
```

### Main.java:
```java
package com.payrollsystem;

import java.time.LocalDateTime;

public class Main {
    public static void main(String[] args) {
        // Tạo TimecardManager để quản lý các Timecard
        TimecardManager manager = new TimecardManager();
        
        // Mô phỏng nhân viên 1 clock in và clock out
        manager.clockIn(101, LocalDateTime.of(2024, 11, 11, 9, 0, 0, 0));
        manager.clockOut(101, LocalDateTime.of(2024, 11, 11, 17, 0, 0, 0));
        
        // Mô phỏng nhân viên 2 clock in và clock out
        manager.clockIn(102, LocalDateTime.of(2024, 11, 11, 8, 30, 0, 0));
        manager.clockOut(102, LocalDateTime.of(2024, 11, 11, 16, 30, 0, 0));
        
        // In ra các thông tin Timecard
        manager.printTimecards();
    }
}
```


