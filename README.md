# TRIỂN KHAI HỆ THỐNG ERP CHO CÔNG TY SOFTWARE
## Giới thiệu

Dự án triển khai phân hệ quản lý nhân sự trên nền tảng Odoo nhằm hỗ trợ doanh nghiệp quản lý toàn diện nhân sự và tự động hóa các quy trình nghiệp vụ.

Mục tiêu của dự án:

- Nâng cao hiệu quả quản lý nhân sự
- Tiết kiệm thời gian và chi phí vận hành
- Hạn chế sai sót thủ công trong các tác vụ nhân sự
- Tự động hóa quy trình nghiệp vụ từ tuyển dụng đến tính lương

Đối tượng sử dụng:

- Phòng nhân sự
- Quản lý cấp trung và cấp cao
- Nhân viên (tra cứu thông tin cá nhân)

## Tính năng
-	Tạo user & phân quyền trên Odoo
- Quản lý tuyển dụng: 
    + Lập kế hoạch tuyển dụng
    + Đăng tin, lọc hồ sơ, lên lịch phỏng vấn, đánh giá ứng viên
- Quản lý hồ sơ nhân viên: Lưu trữ thông tin cá nhân, phòng ban, chức vụ
- Quản lý hợp đồng lao động: Tạo, gia hạn, chấm dứt hợp đồng
- Quản lý chấm công: Ghi nhận giờ vào/ra, tính toán giờ làm việc, overtime
- Quản lý nghỉ phép: Đăng ký, phê duyệt, theo dõi số ngày phép còn lại
- Quản lý tính lương: 
    + Nhập dữ liệu chấm công (CSV)
    + Cấu hình quy tắc tính lương, thuế, bảo hiểm, phụ cấp
    + Cấu hình cấu trúc lương theo phòng ban
    + Tạo phiếu lương theo lô hàng tháng, theo phòng ban
- Báo cáo và thống kê: Dashboard tổng quan, báo cáo chi tiết
- Tích hợp API: Kết nối với các hệ thống bên ngoài

## Cấu trúc dữ liệu

Các loại dữ liệu được xử lý:

### Thông tin tuyển dụng
- Vị trí tuyển dụng, yêu cầu công việc
- Hồ sơ ứng viên, lịch phỏng vấn
- Kết quả đánh giá và quyết định tuyển dụng

### Hồ sơ nhân viên
- Mã nhân viên, thông tin cá nhân (họ tên, ngày sinh, giới tính)
- Thông tin liên lạc (địa chỉ, email, số điện thoại)
- Thông tin công việc (phòng ban, chức vụ, ngày vào làm)

### Hợp đồng lao động
- Loại hợp đồng, thời hạn hợp đồng
- Mức lương cơ bản, các khoản phụ cấp
- Ngày ký và ngày kết thúc hợp đồng

### Dữ liệu chấm công
- Ngày công, giờ vào - giờ ra
- Ca làm việc, thời gian làm thêm
- Trạng thái attendance (có mặt, vắng mặt, trễ)

### Quản lý nghỉ phép
- Loại phép (phép năm, phép ốm, phép đặc biệt)
- Số ngày phép còn lại, ngày nghỉ
- Trạng thái phê duyệt đơn phép

### Dữ liệu tính lương
- Lương cơ bản, thưởng, phạt, phụ cấp
- Thuế thu nhập cá nhân, các khoản bảo hiểm
- Lương thực lĩnh, chi tiết phiếu lương

## Cấu trúc Database (PostgreSQL)

Các bảng chính:

- hr_employee: Lưu thông tin cá nhân và trạng thái nhân viên
- hr_contract: Chứa thông tin hợp đồng lao động
- hr_recruitment: Quản lý quy trình tuyển dụng
- hr_attendance: Lưu trữ dữ liệu chấm công hàng ngày
- hr_leave: Quản lý đơn nghỉ phép và số ngày phép
- hr_payslip: Lưu phiếu lương, thuế, bảo hiểm

Các bảng được liên kết qua khóa ngoại, đảm bảo tính toàn vẹn dữ liệu và khả năng truy xuất đa chiều (theo phòng ban, thời gian, nhân viên).

## Công nghệ sử dụng

- Framework: Odoo 18.3 (Python-based ERP framework)
- Process Modeling: BPMN.io (Business Process Model and Notation)
- Analysis: Use Case Diagrams, UML
- Database: PostgreSQL 13+ (Primary database for Odoo)
- Payroll Rule: Python-based payroll rules engine
