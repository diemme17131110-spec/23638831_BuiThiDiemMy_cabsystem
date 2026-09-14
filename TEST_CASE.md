# CAB System – Test Case

## Tổng quan

Tài liệu này mô tả các Test Case cho hệ thống **CAB System** (MVP 7 tuần), bao phủ các chức năng cốt lõi:

- Account Management
- Ride Booking
- Driver Matching
- Trip Management
- Payment
- Notification
- Rating
- Operations & Security

---

# Module 1 – Account Management (FR01)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC_ACC_001 | Đăng ký tài khoản | Đăng ký thành công | Chưa có tài khoản | 1. Mở Register.<br>2. Nhập thông tin.<br>3. Nhấn Register. | Email: my@gmail.com<br>Password: 123456Aa | Tài khoản được tạo thành công. | High |
| TC_ACC_002 | Đăng ký tài khoản | Email đã tồn tại | Email đã được đăng ký | 1. Mở Register.<br>2. Nhập email đã tồn tại.<br>3. Nhấn Register. | Email: my@gmail.com | Hiển thị thông báo "Email đã tồn tại". | High |
| TC_ACC_003 | Đăng nhập | Đăng nhập thành công | Đã có tài khoản | 1. Mở Login.<br>2. Nhập email.<br>3. Nhập mật khẩu.<br>4. Nhấn Login. | Email hợp lệ<br>Password hợp lệ | Chuyển đến trang Home. | High |
| TC_ACC_004 | Đăng nhập | Sai mật khẩu | Đã có tài khoản | Nhập email đúng và mật khẩu sai rồi Login. | Password: 123abc | Hiển thị lỗi đăng nhập. | High |
| TC_ACC_005 | Đăng nhập | Bỏ trống thông tin | Đang ở màn hình Login | Nhấn Login khi chưa nhập dữ liệu. | Rỗng | Yêu cầu nhập đầy đủ thông tin. | Medium |

---

# Module 2 – Ride Booking (FR04)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC_BOOK_001 | Đặt xe | Đặt xe thành công | Đăng nhập thành công | 1. Nhập điểm đón.<br>2. Nhập điểm đến.<br>3. Chọn loại xe.<br>4. Nhấn Đặt xe. | Điểm đón: IUH<br>Điểm đến: Chợ Bến Thành | Tạo yêu cầu đặt xe thành công. | Critical |
| TC_BOOK_002 | Đặt xe | Thiếu điểm đón | Đăng nhập | Để trống điểm đón rồi đặt xe. | Điểm đến hợp lệ | Không tạo yêu cầu và báo lỗi. | High |
| TC_BOOK_003 | Đặt xe | Thiếu điểm đến | Đăng nhập | Để trống điểm đến rồi đặt xe. | Điểm đón hợp lệ | Không tạo yêu cầu và báo lỗi. | High |
| TC_BOOK_004 | Theo dõi yêu cầu | Kiểm tra trạng thái tìm tài xế | Đã gửi yêu cầu đặt xe | Mở màn hình theo dõi chuyến đi. | — | Hiển thị trạng thái "Đang tìm tài xế". | High |

---

# Module 3 – Driver Matching (FR05)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC_MATCH_001 | Tìm tài xế | Có tài xế phù hợp | Có tài xế sẵn sàng gần khách | Khách hàng gửi yêu cầu đặt xe. | Driver A cách 1 km | Hệ thống gửi yêu cầu cho Driver A. | Critical |
| TC_MATCH_002 | Phân công tài xế | Driver chấp nhận chuyến | Driver nhận được yêu cầu | Driver nhấn **Accept**. | — | Chuyến được phân công cho Driver. | Critical |
| TC_MATCH_003 | Phân công tài xế | Driver từ chối chuyến | Có nhiều tài xế phù hợp | Driver nhấn **Reject**. | — | Hệ thống tìm tài xế tiếp theo. | Critical |
| TC_MATCH_004 | Phân công tài xế | Driver không phản hồi | Driver nhận yêu cầu | Chờ hết thời gian phản hồi. | — | Chuyển yêu cầu sang tài xế khác. | High |
| TC_MATCH_005 | Tìm tài xế | Không còn tài xế | Không có tài xế phù hợp | Gửi yêu cầu đặt xe. | — | Hiển thị thông báo không tìm được tài xế. | High |

---

# Module 4 – Trip Management (FR06)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC_TRIP_001 | Quản lý chuyến | Driver nhận chuyến | Đã được phân công | Driver nhấn **Accept**. | — | Trạng thái chuyển sang **Assigned**. | Critical |
| TC_TRIP_002 | Quản lý chuyến | Driver đến điểm đón | Đã nhận chuyến | Driver cập nhật **Arrived**. | — | Khách nhận thông báo tài xế đã đến. | High |
| TC_TRIP_003 | Quản lý chuyến | Driver đón khách | Driver đã đến điểm đón | Driver cập nhật **Picked Up**. | — | Trạng thái được cập nhật. | High |
| TC_TRIP_004 | Quản lý chuyến | Driver đang di chuyển | Đã đón khách | Driver cập nhật **In Progress**. | — | Khách theo dõi được trạng thái mới. | Medium |
| TC_TRIP_005 | Quản lý chuyến | Hoàn thành chuyến | Đang di chuyển | Driver nhấn **Complete**. | — | Chuyển sang bước tính cước. | Critical |

---

# Module 5 – Payment (FR07)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC_PAY_001 | Thanh toán | Tiền mặt thành công | Chuyến hoàn thành | Chọn thanh toán tiền mặt. | Cash | Thanh toán hoàn tất. | Critical |
| TC_PAY_002 | Thanh toán | Thanh toán điện tử thành công | Chuyến hoàn thành | Chọn thanh toán điện tử. | Ví điện tử | Cập nhật trạng thái thành công. | Critical |
| TC_PAY_003 | Thanh toán | Thanh toán điện tử thất bại | Payment Provider trả lỗi | Thực hiện thanh toán. | Giao dịch lỗi | Hiển thị thông báo thất bại. | High |
| TC_PAY_004 | Thanh toán | Thanh toán lại | Thanh toán thất bại | Nhấn **Retry**. | Phương thức hợp lệ | Thanh toán thành công. | Medium |

---

# Module 6 – Notification (FR08)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC_NOTI_001 | Thông báo | Driver nhận chuyến | Có chuyến mới | Driver Accept. | — | Khách nhận thông báo. | High |
| TC_NOTI_002 | Thông báo | Driver đến điểm đón | Driver Arrived | Cập nhật trạng thái. | — | Khách nhận thông báo. | High |
| TC_NOTI_003 | Thông báo | Thanh toán thành công | Thanh toán hoàn tất | Hoàn thành thanh toán. | — | Hiển thị thông báo thành công. | Medium |

---

# Module 7 – Rating (FR09)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC_RATE_001 | Đánh giá | Đánh giá sau chuyến | Chuyến hoàn thành | Chọn 5 sao rồi gửi. | 5⭐ | Lưu đánh giá thành công. | Medium |
| TC_RATE_002 | Đánh giá | Chưa hoàn thành chuyến | Chuyến chưa kết thúc | Mở màn hình đánh giá. | — | Không cho phép đánh giá. | Medium |

---

# Module 8 – Operations & Security (FR10, FR12)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC_OPS_001 | Quản lý khách hàng | Xem danh sách khách hàng | Đăng nhập Operations Staff | Mở Customer Management. | — | Hiển thị danh sách khách hàng. | Medium |
| TC_OPS_002 | Theo dõi chuyến | Xem chuyến đang diễn ra | Có chuyến hoạt động | Mở Dashboard. | — | Hiển thị trạng thái chuyến. | Medium |
| TC_SEC_001 | Phân quyền | Customer truy cập trang Admin | Đăng nhập Customer | Truy cập `/admin`. | Customer | Bị từ chối truy cập. | Critical |
| TC_SEC_002 | Phân quyền | Admin truy cập trang Admin | Đăng nhập Admin | Truy cập `/admin`. | Admin | Truy cập thành công. | High |

---

# Tổng hợp Test Case

| Module | Số lượng |
|---|---:|
| Account Management | 5 |
| Ride Booking | 4 |
| Driver Matching | 5 |
| Trip Management | 5 |
| Payment | 4 |
| Notification | 3 |
| Rating | 2 |
| Operations & Security | 4 |
| **Tổng cộng** | **32 Test Case** |

---

# Traceability

| Functional Requirement | Test Case |
|---|---|
| FR01 | TC_ACC_001 → TC_ACC_005 |
| FR04 | TC_BOOK_001 → TC_BOOK_004 |
| FR05 | TC_MATCH_001 → TC_MATCH_005 |
| FR06 | TC_TRIP_001 → TC_TRIP_005 |
| FR07 | TC_PAY_001 → TC_PAY_004 |
| FR08 | TC_NOTI_001 → TC_NOTI_003 |
| FR09 | TC_RATE_001 → TC_RATE_002 |
| FR10 | TC_OPS_001 → TC_OPS_002 |
| FR12 | TC_SEC_001 → TC_SEC_002 |
