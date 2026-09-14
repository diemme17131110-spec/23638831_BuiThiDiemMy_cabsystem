# CAB System – Test Case

> Tài liệu mô tả các Test Case cho phiên bản **MVP 7 tuần** của hệ thống CAB System.

## Phân loại Test Case

| Ghi chú | Ý nghĩa |
|---------|---------|
| Positive | Trường hợp hợp lệ |
| Negative | Trường hợp không hợp lệ |
| Validation | Kiểm tra ràng buộc dữ liệu |
| Boundary | Kiểm tra giá trị biên |
| Business Rule | Kiểm tra quy tắc nghiệp vụ |
| Security | Kiểm tra bảo mật |
| Authorization | Kiểm tra phân quyền |
| Exception | Kiểm tra tình huống ngoại lệ |
| Retry | Kiểm tra thực hiện lại |
| API Validation | Kiểm tra API thiếu dữ liệu |
| API Negative | Kiểm tra API với dữ liệu sai |
| UI | Kiểm tra giao diện |

---

# Module 1 – Quản lý tài khoản (FR01)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC-ACC-001 | Người dùng đăng nhập | Đăng nhập với email và mật khẩu hợp lệ | Tài khoản đã đăng ký và đang hoạt động | 1. Mở màn hình Đăng nhập.<br>2. Nhập email.<br>3. Nhập mật khẩu.<br>4. Nhấn Đăng nhập. | Email: `my@gmail.com`<br>Password: `Password@123` | Đăng nhập thành công và chuyển đến trang chủ. | High | Positive |
| TC-ACC-002 | Người dùng đăng nhập | Đăng nhập với email không tồn tại | Hệ thống hoạt động bình thường | 1. Nhập email không tồn tại.<br>2. Nhập mật khẩu.<br>3. Nhấn Đăng nhập. | `unknown@gmail.com` | Hiển thị thông báo thông tin đăng nhập không hợp lệ. | High | Negative |
| TC-ACC-003 | Người dùng đăng nhập | Đăng nhập với mật khẩu sai | Email tồn tại | 1. Nhập email đúng.<br>2. Nhập mật khẩu sai.<br>3. Nhấn Đăng nhập. | `Wrong@123` | Không đăng nhập thành công. | High | Negative |
| TC-ACC-004 | Người dùng đăng nhập | Để trống email | Đang ở màn hình Đăng nhập | 1. Để trống email.<br>2. Nhập mật khẩu.<br>3. Nhấn Đăng nhập. | Email rỗng | Hiển thị lỗi yêu cầu nhập email. | High | Validation |
| TC-ACC-005 | Người dùng đăng nhập | Để trống mật khẩu | Đang ở màn hình Đăng nhập | 1. Nhập email.<br>2. Để trống mật khẩu.<br>3. Nhấn Đăng nhập. | Password rỗng | Hiển thị lỗi yêu cầu nhập mật khẩu. | High | Validation |
| TC-ACC-006 | Người dùng đăng nhập | Để trống cả email và mật khẩu | Đang ở màn hình Đăng nhập | 1. Không nhập dữ liệu.<br>2. Nhấn Đăng nhập. | Rỗng | Hiển thị lỗi cho cả hai trường. | High | Validation |
| TC-ACC-007 | Người dùng đăng nhập | Email sai định dạng | Đang ở màn hình Đăng nhập | 1. Nhập email sai định dạng.<br>2. Nhập mật khẩu.<br>3. Đăng nhập. | `mygmail.com` | Hiển thị lỗi định dạng email. | Medium | Validation |
| TC-ACC-008 | Người dùng đăng nhập | Mật khẩu không đúng định dạng | Quy tắc mật khẩu đã được cấu hình | 1. Nhập email.<br>2. Nhập mật khẩu quá ngắn.<br>3. Đăng nhập. | `123` | Hiển thị lỗi mật khẩu không hợp lệ. | Medium | Boundary |
| TC-ACC-009 | Người dùng đăng nhập | Đăng nhập bằng tài khoản bị khóa | Tài khoản Locked | Nhập thông tin rồi Đăng nhập. | Email hợp lệ | Hiển thị thông báo tài khoản bị khóa. | High | Security |
| TC-ACC-010 | Người dùng đăng nhập | Đăng nhập bằng tài khoản chưa kích hoạt | Tài khoản Inactive | Đăng nhập bằng tài khoản chưa kích hoạt. | Email Inactive | Thông báo tài khoản chưa hoạt động. | High | Negative |
| TC-ACC-011 | Người dùng đăng nhập | Kiểm tra chữ hoa/chữ thường của email | Có quy tắc xử lý email | Nhập email khác kiểu chữ. | `My@Gmail.com` | Xử lý đúng theo quy tắc hệ thống. | Medium | Business Rule |
| TC-ACC-012 | Người dùng đăng nhập | Kiểm tra chữ hoa/chữ thường của mật khẩu | Tài khoản hoạt động | Nhập mật khẩu khác kiểu chữ. | `password@123` | Đăng nhập thất bại nếu phân biệt hoa/thường. | High | Security |
| TC-ACC-013 | Người dùng đăng nhập | Mật khẩu có khoảng trắng đầu/cuối | Tài khoản hoạt động | Nhập mật khẩu có khoảng trắng. | `" Password@123 "` | Hệ thống xử lý đúng theo quy tắc. | Medium | Boundary |
| TC-ACC-014 | Người dùng đăng nhập | Kiểm tra ô mật khẩu được che | Đang ở màn hình Đăng nhập | Nhập mật khẩu vào ô Password. | `Password@123` | Mật khẩu hiển thị dạng dấu chấm (*). | Medium | UI |
| TC-ACC-015 | Người dùng đăng nhập | Truy cập chức năng sau khi đăng nhập | Có quyền truy cập | Đăng nhập rồi mở chức năng được cấp quyền. | Email hợp lệ | Truy cập thành công. | High | Authorization |
| TC-ACC-016 | Người dùng đăng nhập | Đăng nhập sai nhiều lần | Có cơ chế giới hạn số lần sai | Nhập sai mật khẩu liên tiếp. | `Wrong@123` | Khóa tài khoản hoặc áp dụng cơ chế bảo vệ. | High | Security |
| TC-ACC-017 | API đăng nhập | Thiếu trường email | API Login hoạt động | Gửi request không có email. | `{password:"Password@123"}` | API trả lỗi xác thực. | High | API Validation |
| TC-ACC-018 | API đăng nhập | Thiếu trường mật khẩu | API Login hoạt động | Gửi request không có mật khẩu. | `{email:"my@gmail.com"}` | API trả lỗi xác thực. | High | API Validation |
| TC-ACC-019 | API đăng nhập | Email và mật khẩu không hợp lệ | API Login hoạt động | Gửi request sai dữ liệu. | `unknown + wrong` | Không tạo token. | High | API Negative |
| TC-ACC-020 | API đăng nhập | Kiểm tra dữ liệu trả về | Đăng nhập thành công | Gửi request hợp lệ rồi kiểm tra response. | Email hợp lệ | Response không chứa mật khẩu hoặc dữ liệu nhạy cảm. | High | Security |

---

# Module 2 – Đặt xe (FR04)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC-BOOK-001 | Đặt xe | Đặt xe thành công | Đăng nhập | 1. Nhập điểm đón.<br>2. Nhập điểm đến.<br>3. Chọn loại xe.<br>4. Nhấn Đặt xe. | IUH → Chợ Bến Thành | Tạo yêu cầu thành công. | Critical | Positive |
| TC-BOOK-002 | Đặt xe | Thiếu điểm đón | Đăng nhập | Để trống điểm đón rồi Đặt xe. | Điểm đến hợp lệ | Báo lỗi. | High | Validation |
| TC-BOOK-003 | Đặt xe | Thiếu điểm đến | Đăng nhập | Để trống điểm đến rồi Đặt xe. | Điểm đón hợp lệ | Báo lỗi. | High | Validation |
| TC-BOOK-004 | Theo dõi chuyến | Kiểm tra trạng thái tìm tài xế | Đã gửi yêu cầu | Mở màn hình theo dõi. | — | Hiển thị "Đang tìm tài xế". | High | Positive |
| TC-BOOK-005 | Đặt xe | Điểm đón trùng điểm đến | Đăng nhập | Nhập cùng địa điểm. | IUH → IUH | Báo lỗi. | Medium | Validation |
| TC-BOOK-006 | Hủy chuyến | Hủy khi đang tìm tài xế | Có yêu cầu | Nhấn Hủy chuyến. | — | Chuyến bị hủy. | High | Business Rule |

---

# Module 3 – Tìm và phân công tài xế (FR05)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC-MATCH-001 | Tìm tài xế | Có tài xế phù hợp | Có tài xế gần khách | Gửi yêu cầu đặt xe. | Driver cách 1 km | Gửi yêu cầu cho Driver. | Critical | Positive |
| TC-MATCH-002 | Phân công | Driver chấp nhận | Driver nhận yêu cầu | Nhấn Accept. | — | Chuyến được phân công. | Critical | Positive |
| TC-MATCH-003 | Phân công | Driver từ chối | Có nhiều Driver | Nhấn Reject. | — | Tìm Driver tiếp theo. | Critical | Business Rule |
| TC-MATCH-004 | Phân công | Driver không phản hồi | Driver nhận yêu cầu | Chờ hết thời gian phản hồi. | — | Chuyển sang Driver khác. | High | Exception |
| TC-MATCH-005 | Tìm tài xế | Không còn tài xế | Không có Driver | Gửi yêu cầu. | — | Báo không tìm được tài xế. | High | Negative |
| TC-MATCH-006 | Tìm tài xế | Ưu tiên tài xế gần nhất | Có nhiều Driver | Gửi yêu cầu. | Driver A cách 500m | Driver gần nhất được chọn. | High | Business Rule |
| TC-MATCH-007 | Tìm tài xế | Driver không sẵn sàng | Driver Offline | Gửi yêu cầu. | Offline | Không phân công. | High | Negative |

---

# Module 4 – Quản lý chuyến đi (FR06)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC-TRIP-001 | Quản lý chuyến | Driver nhận chuyến | Đã phân công | Nhấn Accept. | — | Trạng thái "Đã phân công". | Critical | Positive |
| TC-TRIP-002 | Quản lý chuyến | Driver đến điểm đón | Đã nhận chuyến | Cập nhật "Đã đến". | — | Khách nhận thông báo. | High | Positive |
| TC-TRIP-003 | Quản lý chuyến | Driver đón khách | Đã đến điểm đón | Cập nhật "Đã đón khách". | — | Trạng thái cập nhật. | High | Positive |
| TC-TRIP-004 | Quản lý chuyến | Driver đang di chuyển | Đã đón khách | Cập nhật "Đang di chuyển". | — | Khách thấy trạng thái mới. | Medium | Positive |
| TC-TRIP-005 | Quản lý chuyến | Hoàn thành chuyến | Đang di chuyển | Nhấn Hoàn thành. | — | Chuyển sang tính cước. | Critical | Positive |
| TC-TRIP-006 | Quản lý chuyến | Cập nhật sai thứ tự trạng thái | Đã nhận chuyến | Chọn Hoàn thành ngay. | — | Không cho phép. | High | Business Rule |
| TC-TRIP-007 | Theo dõi chuyến | Hiển thị ETA | Có chuyến | Mở theo dõi chuyến. | — | Hiển thị thời gian dự kiến. | Medium | Positive |

---

# Module 5 – Thanh toán (FR07)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC-PAY-001 | Thanh toán | Tiền mặt thành công | Chuyến hoàn thành | Chọn Tiền mặt. | Cash | Thanh toán hoàn tất. | Critical | Positive |
| TC-PAY-002 | Thanh toán | Điện tử thành công | Chuyến hoàn thành | Chọn Ví điện tử. | Ví điện tử | Thành công. | Critical | Positive |
| TC-PAY-003 | Thanh toán | Điện tử thất bại | Payment trả lỗi | Thanh toán. | Giao dịch lỗi | Báo thất bại. | High | Exception |
| TC-PAY-004 | Thanh toán | Thanh toán lại | Thanh toán thất bại | Nhấn Retry. | Hợp lệ | Thành công. | Medium | Retry |
| TC-PAY-005 | Thanh toán | Chọn sai phương thức | Chuyến hoàn thành | Chọn phương thức lỗi. | — | Báo lỗi. | Medium | Exception |
| TC-PAY-006 | Thanh toán | Payment không phản hồi | Có giao dịch | Thanh toán. | Timeout | Hiển thị trạng thái chờ. | High | Exception |

---

# Module 6 – Thông báo (FR08)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC-NOTI-001 | Thông báo | Driver nhận chuyến | Có chuyến mới | Driver Accept. | — | Khách nhận thông báo. | High | Positive |
| TC-NOTI-002 | Thông báo | Driver đến điểm đón | Driver Arrived | Cập nhật trạng thái. | — | Khách nhận thông báo. | High | Positive |
| TC-NOTI-003 | Thông báo | Thanh toán thành công | Thanh toán xong | Hoàn tất thanh toán. | — | Báo thành công. | Medium | Positive |
| TC-NOTI-004 | Thông báo | Không gửi trùng thông báo | Đã gửi trước đó | Kiểm tra log. | — | Chỉ gửi một lần. | Medium | Business Rule |
| TC-NOTI-005 | Thông báo | Không tìm được tài xế | Không có Driver | Gửi yêu cầu. | — | Khách nhận thông báo. | High | Positive |

---

# Module 7 – Đánh giá tài xế (FR09)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC-RATE-001 | Đánh giá | Đánh giá 5 sao | Chuyến hoàn thành | Chọn 5 sao → Gửi. | ⭐⭐⭐⭐⭐ | Lưu thành công. | Medium | Positive |
| TC-RATE-002 | Đánh giá | Chưa hoàn thành chuyến | Chuyến chưa kết thúc | Mở đánh giá. | — | Không cho phép. | Medium | Business Rule |
| TC-RATE-003 | Đánh giá | Đánh giá 1 sao | Chuyến hoàn thành | Chọn 1 sao. | ⭐ | Lưu thành công. | Medium | Positive |
| TC-RATE-004 | Đánh giá | Gửi đánh giá hai lần | Đã đánh giá | Mở lại màn hình. | — | Không cho phép gửi lại. | Medium | Business Rule |

---

# Module 8 – Quản lý vận hành và bảo mật (FR10, FR12)

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | Ghi chú |
|---|---|---|---|---|---|---|---|---|
| TC-OPS-001 | Quản lý khách hàng | Xem danh sách khách hàng | Nhân viên đã đăng nhập | Mở Quản lý khách hàng. | — | Hiển thị danh sách. | Medium | Positive |
| TC-OPS-002 | Theo dõi chuyến | Xem chuyến đang diễn ra | Có chuyến hoạt động | Mở Dashboard. | — | Hiển thị trạng thái. | Medium | Positive |
| TC-OPS-003 | Quản lý tài xế | Tìm kiếm tài xế | Nhân viên đã đăng nhập | Nhập từ khóa. | Driver A | Hiển thị kết quả. | Low | Positive |
| TC-SEC-001 | Phân quyền | Customer truy cập Admin | Customer đăng nhập | Truy cập `/admin`. | Customer | Từ chối truy cập. | Critical | Authorization |
| TC-SEC-002 | Phân quyền | Admin truy cập Admin | Admin đăng nhập | Truy cập `/admin`. | Admin | Truy cập thành công. | High | Authorization |
| TC-SEC-003 | Bảo mật | Truy cập URL quản trị | Customer đăng nhập | Mở `/admin/users`. | Customer | Từ chối truy cập. | Critical | Authorization |
| TC-SEC-004 | Bảo mật | Phiên đăng nhập hết hạn | Đã đăng nhập | Chờ hết phiên. | — | Yêu cầu đăng nhập lại. | High | Security |
| TC-SEC-005 | Bảo mật | Kiểm tra Audit Log | Admin thực hiện thao tác | Thay đổi dữ liệu quản trị. | — | Audit Log được lưu. | High | Security |

---

# Thống kê Test Case

| Module | Số lượng |
|---|---:|
| Quản lý tài khoản | 20 |
| Đặt xe | 6 |
| Tìm và phân công tài xế | 7 |
| Quản lý chuyến đi | 7 |
| Thanh toán | 6 |
| Thông báo | 5 |
| Đánh giá tài xế | 4 |
| Quản lý vận hành và bảo mật | 8 |
| **Tổng cộng** | **63 Test Case** |

---

# Thống kê theo loại Test Case

| Loại | Số lượng |
|---|---:|
| Positive | 28 |
| Negative | 5 |
| Validation | 5 |
| Boundary | 2 |
| Business Rule | 6 |
| Security | 6 |
| Authorization | 3 |
| Exception | 4 |
| Retry | 1 |
| API Validation | 2 |
| API Negative | 1 |
| UI | 1 |
| **Tổng** | **63** |

---

# Ma trận truy vết (Traceability)

| Functional Requirement | Test Case |
|---|---|
| FR01 | TC-ACC-001 → TC-ACC-020 |
| FR04 | TC-BOOK-001 → TC-BOOK-006 |
| FR05 | TC-MATCH-001 → TC-MATCH-007 |
| FR06 | TC-TRIP-001 → TC-TRIP-007 |
| FR07 | TC-PAY-001 → TC-PAY-006 |
| FR08 | TC-NOTI-001 → TC-NOTI-005 |
| FR09 | TC-RATE-001 → TC-RATE-004 |
| FR10 | TC-OPS-001 → TC-OPS-003 |
| FR12 | TC-SEC-001 → TC-SEC-005 |
