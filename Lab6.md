# Thiết kế chi tiết các lớp trong Payroll System
## 1. Ca sử dụng Maintain Timecard
**Lớp `Employee`**  
- **Thuộc tính**:  
  - `id: int`
  - `name: String`
  - `address: String`
  - `paymentMethod: PaymentMethod`

**Lớp `Timecard`**  
- **Thuộc tính**:  
  - `id: int`
  - `employeeId: int`
  - `date: Date`
  - `hoursWorked: double`

**Lớp `TimecardService`**  
- **Thuộc tính**:  
  - Không cần thuộc tính (lớp service xử lý logic).

---
## 2. 
