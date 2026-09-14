# CAB System – Test Case

> Tài liệu mô tả các Test Case cho phiên bản **MVP 7 tuần** của hệ thống CAB System.

## Mục lục

- Module 1 – Quản lý tài khoản
- Module 2 – Đặt xe
- Module 3 – Tìm và phân công tài xế
- Module 4 – Quản lý chuyến đi
- Module 5 – Thanh toán
- Module 6 – Thông báo
- Module 7 – Đánh giá tài xế
- Module 8 – Quản lý vận hành và bảo mật
- Thống kê Test Case
- Ma trận truy vết

---

# Module 1 – Quản lý tài khoản (FR01)

| Test Case ID | Test Scenario | Test Case | Điều kiện trước | Các bước thực hiện | Dữ liệu kiểm thử | Kết quả mong đợi | Ưu tiên | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC_ACC_001 | Đăng ký | Đăng ký thành công | Chưa có tài khoản | Mở Register → Nhập thông tin → Register | Email: my@gmail.com Password: 123456Aa | Tạo tài khoản thành công | Cao | Positive |
| TC_ACC_002 | Đăng ký | Email đã tồn tại | Email đã đăng ký | Nhập email đã tồn tại rồi Register | my@gmail.com | Báo "Email đã tồn tại" | Cao | Negative |
| TC_ACC_003 | Đăng nhập | Đăng nhập thành công | Có tài khoản | Nhập email và mật khẩu → Login | Hợp lệ | Chuyển đến trang chủ | Cao | Positive |
| TC_ACC_004 | Đăng nhập | Sai mật khẩu | Có tài khoản | Nhập sai mật khẩu | 123abc | Báo lỗi đăng nhập | Cao | Negative |
| TC_ACC_005 | Đăng nhập | Bỏ trống thông tin | Đang ở Login | Nhấn Login khi chưa nhập | Rỗng | Yêu cầu nhập đầy đủ | Trung bình | Validation |
| TC_ACC_006 | Đăng ký | Email sai định dạng | Chưa có tài khoản | Nhập email sai rồi Register | mygmail.com | Báo email không hợp lệ | Trung bình | Validation |
| TC_ACC_007 | Đăng ký | Mật khẩu quá ngắn | Chưa có tài khoản | Nhập mật khẩu ngắn | 12345 | Báo lỗi mật khẩu | Trung bình | Boundary |
| TC_ACC_008 | Đăng nhập | Tài khoản bị khóa | Tài khoản bị khóa | Đăng nhập | Tài khoản khóa | Từ chối đăng nhập | Cao | Security |

---

# Module 2 – Đặt xe (FR04)

| Test Case ID | Test Scenario | Test Case | Điều kiện trước | Các bước thực hiện | Dữ liệu kiểm thử | Kết quả mong đợi | Ưu tiên | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC_BOOK_001 | Đặt xe | Đặt xe thành công | Đăng nhập | Nhập điểm đón → Điểm đến → Chọn xe → Đặt xe | IUH → Chợ Bến Thành | Tạo yêu cầu thành công | Rất cao | Positive |
| TC_BOOK_002 | Đặt xe | Thiếu điểm đón | Đăng nhập | Để trống điểm đón | Điểm đến hợp lệ | Báo lỗi | Cao | Validation |
| TC_BOOK_003 | Đặt xe | Thiếu điểm đến | Đăng nhập | Để trống điểm đến | Điểm đón hợp lệ | Báo lỗi | Cao | Validation |
| TC_BOOK_004 | Theo dõi chuyến | Kiểm tra trạng thái tìm tài xế | Đã gửi yêu cầu | Mở màn hình theo dõi | — | Hiển thị "Đang tìm tài xế" | Cao | Positive |
| TC_BOOK_005 | Đặt xe | Điểm đón trùng điểm đến | Đăng nhập | Nhập cùng địa điểm | IUH → IUH | Báo lỗi | Trung bình | Validation |
| TC_BOOK_006 | Hủy chuyến | Hủy khi đang tìm tài xế | Có yêu cầu | Nhấn Hủy | — | Chuyến bị hủy | Cao | Business Rule |

---

# Module 3 – Tìm và phân công tài xế (FR05)

| Test Case ID | Test Scenario | Test Case | Điều kiện trước | Các bước thực hiện | Dữ liệu kiểm thử | Kết quả mong đợi | Ưu tiên | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC_MATCH_001 | Tìm tài xế | Có tài xế phù hợp | Có tài xế gần | Gửi yêu cầu | Driver cách 1 km | Gửi yêu cầu cho Driver | Rất cao | Positive |
| TC_MATCH_002 | Phân công | Driver chấp nhận | Driver nhận yêu cầu | Nhấn Accept | — | Chuyến được phân công | Rất cao | Positive |
| TC_MATCH_003 | Phân công | Driver từ chối | Có nhiều tài xế | Nhấn Reject | — | Tìm tài xế tiếp theo | Rất cao | Business Rule |
| TC_MATCH_004 | Phân công | Driver không phản hồi | Driver nhận yêu cầu | Chờ hết thời gian | — | Chuyển sang Driver khác | Cao | Exception |
| TC_MATCH_005 | Tìm tài xế | Không còn tài xế | Không có Driver | Gửi yêu cầu | — | Báo không tìm được tài xế | Cao | Negative |
| TC_MATCH_006 | Tìm tài xế | Ưu tiên tài xế gần nhất | Có nhiều Driver | Gửi yêu cầu | Driver A cách 500m | Driver gần nhất được chọn | Cao | Business Rule |
| TC_MATCH_007 | Tìm tài xế | Driver không sẵn sàng | Driver Offline | Gửi yêu cầu | Offline | Không phân công | Cao | Negative |

---

# Module 4 – Quản lý chuyến đi (FR06)

| Test Case ID | Test Scenario | Test Case | Điều kiện trước | Các bước thực hiện | Dữ liệu kiểm thử | Kết quả mong đợi | Ưu tiên | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC_TRIP_001 | Quản lý chuyến | Driver nhận chuyến | Đã phân công | Nhấn Accept | — | Trạng thái "Đã phân công" | Rất cao | Positive |
| TC_TRIP_002 | Quản lý chuyến | Driver đến điểm đón | Đã nhận chuyến | Cập nhật "Đã đến" | — | Khách nhận thông báo | Cao | Positive |
| TC_TRIP_003 | Quản lý chuyến | Driver đón khách | Đã đến điểm đón | Cập nhật "Đã đón khách" | — | Trạng thái cập nhật | Cao | Positive |
| TC_TRIP_004 | Quản lý chuyến | Driver đang di chuyển | Đã đón khách | Cập nhật "Đang di chuyển" | — | Khách thấy trạng thái mới | Trung bình | Positive |
| TC_TRIP_005 | Quản lý chuyến | Hoàn thành chuyến | Đang di chuyển | Nhấn Hoàn thành | — | Chuyển sang tính cước | Rất cao | Positive |
| TC_TRIP_006 | Quản lý chuyến | Cập nhật sai thứ tự trạng thái | Đã nhận chuyến | Chọn Hoàn thành ngay | — | Không cho phép | Cao | Business Rule |
| TC_TRIP_007 | Theo dõi chuyến | Hiển thị ETA | Có chuyến | Mở theo dõi | — | Hiển thị thời gian dự kiến | Trung bình | Positive |

---

# Module 5 – Thanh toán (FR07)

| Test Case ID | Test Scenario | Test Case | Điều kiện trước | Các bước thực hiện | Dữ liệu kiểm thử | Kết quả mong đợi | Ưu tiên | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC_PAY_001 | Thanh toán | Tiền mặt thành công | Chuyến hoàn thành | Chọn Tiền mặt | Cash | Thanh toán hoàn tất | Rất cao | Positive |
| TC_PAY_002 | Thanh toán | Điện tử thành công | Chuyến hoàn thành | Chọn Ví điện tử | Ví điện tử | Cập nhật thành công | Rất cao | Positive |
| TC_PAY_003 | Thanh toán | Điện tử thất bại | Payment trả lỗi | Thanh toán | Giao dịch lỗi | Báo thất bại | Cao | Exception |
| TC_PAY_004 | Thanh toán | Thanh toán lại | Thanh toán thất bại | Nhấn Thử lại | Hợp lệ | Thành công | Trung bình | Retry |
| TC_PAY_005 | Thanh toán | Chọn sai phương thức | Chuyến hoàn thành | Chọn phương thức lỗi | — | Báo lỗi | Trung bình | Exception |
| TC_PAY_006 | Thanh toán | Payment không phản hồi | Có giao dịch | Thanh toán | Timeout | Hiển thị trạng thái chờ | Cao | Exception |

---

# Module 6 – Thông báo (FR08)

| Test Case ID | Test Scenario | Test Case | Điều kiện trước | Các bước thực hiện | Dữ liệu kiểm thử | Kết quả mong đợi | Ưu tiên | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC_NOTI_001 | Thông báo | Driver nhận chuyến | Có chuyến mới | Driver Accept | — | Khách nhận thông báo | Cao | Positive |
| TC_NOTI_002 | Thông báo | Driver đến điểm đón | Driver Arrived | Cập nhật trạng thái | — | Khách nhận thông báo | Cao | Positive |
| TC_NOTI_003 | Thông báo | Thanh toán thành công | Thanh toán xong | Hoàn tất thanh toán | — | Báo thành công | Trung bình | Positive |
| TC_NOTI_004 | Thông báo | Không gửi trùng thông báo | Đã gửi trước đó | Kiểm tra log | — | Chỉ gửi một lần | Trung bình | Business Rule |
| TC_NOTI_005 | Thông báo | Không tìm được tài xế | Không có Driver | Gửi yêu cầu | — | Khách nhận thông báo | Cao | Positive |

---

# Module 7 – Đánh giá tài xế (FR09)

| Test Case ID | Test Scenario | Test Case | Điều kiện trước | Các bước thực hiện | Dữ liệu kiểm thử | Kết quả mong đợi | Ưu tiên | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC_RATE_001 | Đánh giá | Đánh giá 5 sao | Chuyến hoàn thành | Chọn 5 sao → Gửi | ⭐⭐⭐⭐⭐ | Lưu thành công | Trung bình | Positive |
| TC_RATE_002 | Đánh giá | Chưa hoàn thành chuyến | Chuyến chưa kết thúc | Mở đánh giá | — | Không cho phép | Trung bình | Business Rule |
| TC_RATE_003 | Đánh giá | Đánh giá 1 sao | Chuyến hoàn thành | Chọn 1 sao | ⭐ | Lưu thành công | Trung bình | Positive |
| TC_RATE_004 | Đánh giá | Gửi đánh giá hai lần | Đã đánh giá | Mở lại màn hình | — | Không cho phép gửi lại | Trung bình | Business Rule |

---

# Module 8 – Quản lý vận hành và bảo mật (FR10, FR12)

| Test Case ID | Test Scenario | Test Case | Điều kiện trước | Các bước thực hiện | Dữ liệu kiểm thử | Kết quả mong đợi | Ưu tiên | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC_OPS_001 | Quản lý khách hàng | Xem danh sách | Đăng nhập nhân viên | Mở Quản lý khách hàng | — | Hiển thị danh sách | Trung bình | Positive |
| TC_OPS_002 | Theo dõi chuyến | Xem chuyến đang diễn ra | Có chuyến | Mở Dashboard | — | Hiển thị trạng thái | Trung bình | Positive |
| TC_OPS_003 | Quản lý tài xế | Tìm kiếm tài xế | Đăng nhập nhân viên | Nhập từ khóa | Driver A | Hiển thị kết quả | Thấp | Positive |
| TC_SEC_001 | Phân quyền | Customer vào Admin | Customer đăng nhập | Truy cập `/admin` | Customer | Từ chối truy cập | Rất cao | Authorization |
| TC_SEC_002 | Phân quyền | Admin vào Admin | Admin đăng nhập | Truy cập `/admin` | Admin | Truy cập thành công | Cao | Authorization |
| TC_SEC_003 | Bảo mật | Truy cập URL quản trị | Customer đăng nhập | Mở `/admin/users` | Customer | Từ chối | Rất cao | Authorization |
| TC_SEC_004 | Bảo mật | Phiên đăng nhập hết hạn | Đã đăng nhập | Chờ hết phiên | — | Yêu cầu đăng nhập lại | Cao | Security |
| TC_SEC_005 | Bảo mật | Ghi nhận Audit Log | Admin thao tác quản trị | Thực hiện thay đổi | — | Audit Log được lưu | Cao | Security |

---

# Thống kê Test Case

| Module | Số lượng |
|---|---:|
| Quản lý tài khoản | 8 |
| Đặt xe | 6 |
| Tìm và phân công tài xế | 7 |
| Quản lý chuyến đi | 7 |
| Thanh toán | 6 |
| Thông báo | 5 |
| Đánh giá tài xế | 4 |
| Quản lý vận hành và bảo mật | 8 |
| **Tổng cộng** | **51 Test Case** |

---

# Thống kê theo loại Test Case

| Loại | Số lượng |
|---|---:|
| Positive | 26 |
| Negative | 4 |
| Validation | 4 |
| Boundary | 1 |
| Business Rule | 6 |
| Security | 3 |
| Authorization | 3 |
| Exception | 4 |
| Retry | 1 |
| **Tổng** | **51** |

---

# Ma trận truy vết (Traceability)

| Yêu cầu chức năng | Test Case |
|---|---|
| FR01 | TC_ACC_001 → TC_ACC_008 |
| FR04 | TC_BOOK_001 → TC_BOOK_006 |
| FR05 | TC_MATCH_001 → TC_MATCH_007 |
| FR06 | TC_TRIP_001 → TC_TRIP_007 |
| FR07 | TC_PAY_001 → TC_PAY_006 |
| FR08 | TC_NOTI_001 → TC_NOTI_005 |
| FR09 | TC_RATE_001 → TC_RATE_004 |
| FR10 | TC_OPS_001 → TC_OPS_003 |
| FR12 | TC_SEC_001 → TC_SEC_005 |

---

## Kết luận

Bộ Test Case này bao phủ đầy đủ các chức năng cốt lõi của **CAB System** trong phạm vi **MVP 7 tuần**, bao gồm cả trường hợp hợp lệ, không hợp lệ, kiểm tra ràng buộc dữ liệu, quy tắc nghiệp vụ và bảo mật.
