# 23638831_BuiThiDiemMy_cabsystem
# Dự án xây dựng hệ thống CAB System – Nền tảng đặt xe
## 1. Các bên liên quan

## 1. Các bên liên quan

| Các bên liên quan (Stakeholders) | Vai trò (Role) | Tầm quan trọng |
|---|---|---|
| **Ban giám đốc (Management)** | Đưa ra mục tiêu, định hướng, ngân sách và phê duyệt các yêu cầu chính của hệ thống | **Rất cao** |
| **Khách hàng (Customer)** | Đăng ký, đặt xe, theo dõi chuyến đi, thanh toán, xem lịch sử và đánh giá tài xế | **Rất cao** |
| **Tài xế (Driver)** | Nhận/từ chối chuyến, cập nhật trạng thái chuyến, thông tin phương tiện và vị trí | **Rất cao** |
| **Nhân viên vận hành (Operations Staff)** | Quản lý khách hàng, tài xế, phương tiện, chuyến đi và xử lý sự cố | **Rất cao** |
| **Quản trị viên hệ thống (System Administrator)** | Quản lý tài khoản, phân quyền, cấu hình và bảo mật hệ thống | **Cao** |
| **Business Analyst (BA)** | Thu thập, phân tích, làm rõ và đặc tả yêu cầu | **Cao** |
| **Nhóm phát triển (Development Team)** | Thiết kế, xây dựng, tích hợp và triển khai hệ thống | **Cao** |
| **Nhóm kiểm thử (QA/Tester)** | Kiểm thử chức năng, hiệu năng, bảo mật và độ ổn định | **Cao** |
| **Nhà cung cấp thanh toán (Payment Provider)** | Xử lý các giao dịch thanh toán điện tử | **Cao** |
| **Nhà cung cấp bản đồ/GPS (Map & GPS Provider)** | Cung cấp dữ liệu vị trí, khoảng cách và hỗ trợ tìm tài xế | **Cao** |
| **Nhà cung cấp thông báo (Notification Provider)** | Gửi thông báo đến khách hàng và tài xế | **Trung bình – Cao** |
## 2. Stakeholder Matrix

```mermaid
quadrantChart
    title CAB System - Stakeholder Matrix
    x-axis "Low Interest" --> "High Interest"
    y-axis "Low Power" --> "High Power"

    quadrant-1 "Manage Closely"
    quadrant-2 "Keep Satisfied"
    quadrant-3 "Monitor"
    quadrant-4 "Keep Informed"

    "Ban giám đốc": [0.90, 0.95]
    "Nhân viên vận hành": [0.90, 0.80]
    "Quản trị viên": [0.75, 0.85]
    "Business Analyst": [0.85, 0.75]
    "Khách hàng": [0.95, 0.60]
    "Tài xế": [0.90, 0.60]
    "Payment Provider": [0.55, 0.65]
    "Map/GPS Provider": [0.50, 0.55]
    "Notification Provider": [0.40, 0.45]
    "Development Team": [0.70, 0.70]
    "QA/Tester": [0.65, 0.55]
```

---

---

## 3. Stakeholder quan trọng nhất

| Stakeholder | Mức độ quan trọng | Lý do |
|---|---|---|
| **Management** | ⭐⭐⭐⭐⭐ | Có quyền quyết định và phê duyệt dự án |
| **Customer** | ⭐⭐⭐⭐⭐ | Người sử dụng dịch vụ đặt xe |
| **Driver** | ⭐⭐⭐⭐⭐ | Người trực tiếp thực hiện chuyến xe |
| **Operations Staff** | ⭐⭐⭐⭐⭐ | Quản lý và xử lý hoạt động vận hành |
| **System Administrator** | ⭐⭐⭐⭐ | Quản lý hệ thống, tài khoản và phân quyền |
| **Business Analyst** | ⭐⭐⭐⭐ | Phân tích và làm rõ yêu cầu |
| **Development Team** | ⭐⭐⭐⭐ | Xây dựng hệ thống |
| **QA/Tester** | ⭐⭐⭐⭐ | Đảm bảo chất lượng hệ thống |
| **Payment Provider** | ⭐⭐⭐⭐ | Xử lý thanh toán điện tử |
| **Map/GPS Provider** | ⭐⭐⭐⭐ | Hỗ trợ định vị và tìm tài xế |
| **Notification Provider** | ⭐⭐⭐ | Hỗ trợ gửi thông báo |

# Customer and System Expectations

## 1. Customer Expectations

- **Easy booking:** Khách hàng có thể đăng ký, đăng nhập, nhập điểm đón, điểm đến và chọn loại xe.
- **Trip tracking:** Khách hàng có thể theo dõi trạng thái chuyến đi.
- **Fast driver matching:** Hệ thống tìm tài xế phù hợp và gần khách hàng.
- **Automatic re-matching:** Nếu tài xế từ chối hoặc không phản hồi, hệ thống tiếp tục tìm tài xế khác.
- **Clear notification:** Khách hàng được thông báo khi có tài xế, tài xế đến, chuyến hoàn thành và thanh toán.
- **Flexible payment:** Hỗ trợ thanh toán tiền mặt và thanh toán điện tử.
- **Trip history:** Khách hàng có thể xem lịch sử chuyến đi và số tiền phải trả.
- **Driver rating:** Khách hàng có thể đánh giá tài xế sau chuyến đi.
- **Data security:** Thông tin cá nhân, vị trí và giao dịch được bảo vệ.

## 2. System Expectations

- **Scalability:** Phục vụ số lượng lớn khách hàng và tài xế.
- **Automatic driver matching:** Tự động tìm và ưu tiên tài xế phù hợp.
- **Trip management:** Quản lý toàn bộ trạng thái chuyến đi.
- **Fare and payment management:** Tính cước và hỗ trợ nhiều phương thức thanh toán.
- **Third-party integration:** Có khả năng tích hợp với các nhà cung cấp bên ngoài.
- **Independent scalability:** Các thành phần có thể mở rộng độc lập.
- **High availability:** Lỗi ở một thành phần không làm toàn bộ hệ thống ngừng hoạt động.
- **Security:** Xác thực, phân quyền và bảo vệ dữ liệu.
- **Audit logging:** Lưu vết các thao tác quan trọng.
- **Administration:** Hỗ trợ nhân viên vận hành quản lý hệ thống.
- **Reporting:** Cung cấp báo cáo về chuyến đi, doanh thu, tỷ lệ hoàn thành và hủy chuyến.
- **Future extensibility:** Có thể thêm dịch vụ, phương thức thanh toán và nhà cung cấp mới.



# CAB System – Mục đích nghiệp vụ và yêu cầu hệ thống

## 1. Mục đích của nghiệp vụ

Xây dựng hệ thống **CAB System** nhằm tự động hóa và quản lý toàn bộ quy trình đặt xe, từ khi khách hàng tạo yêu cầu đến khi chuyến đi hoàn thành, thanh toán và đánh giá.

### Mục tiêu cụ thể

- Tự động hóa việc tìm kiếm và phân công tài xế.
- Giảm sự phụ thuộc vào việc phân công tài xế thủ công.
- Giúp khách hàng đặt xe và theo dõi chuyến đi dễ dàng.
- Quản lý tập trung khách hàng, tài xế, phương tiện, chuyến đi và giao dịch.
- Hỗ trợ thanh toán bằng tiền mặt và phương thức điện tử.
- Cung cấp thông báo kịp thời cho khách hàng và tài xế.
- Hỗ trợ nhân viên vận hành quản lý và xử lý sự cố.
- Cung cấp báo cáo về hoạt động kinh doanh.
- Đảm bảo hệ thống bảo mật, ổn định và có khả năng mở rộng.
- Cho phép bổ sung các tính năng mới trong tương lai.

---

# 2. Nghiệp vụ cần làm những gì?

## 2.1. Quản lý khách hàng

- Đăng ký tài khoản.
- Đăng nhập.
- Cập nhật thông tin cá nhân.
- Xem lịch sử chuyến đi.
- Xem số tiền phải trả.
- Đánh giá tài xế sau khi hoàn thành chuyến.

## 2.2. Đặt xe

- Nhập điểm đón.
- Nhập điểm đến.
- Lựa chọn loại xe/dịch vụ.
- Gửi yêu cầu đặt xe.
- Theo dõi trạng thái yêu cầu đặt xe.

## 2.3. Tìm và phân công tài xế

- Xác định các tài xế phù hợp.
- Kiểm tra vị trí của tài xế.
- Kiểm tra trạng thái sẵn sàng của tài xế.
- Áp dụng các tiêu chí vận hành.
- Ưu tiên tài xế phù hợp và gần khách hàng.
- Gửi yêu cầu chuyến đi cho tài xế.
- Nếu tài xế không phản hồi hoặc từ chối, tiếp tục tìm tài xế khác.
- Nếu không tìm được tài xế, thông báo cho khách hàng.

## 2.4. Thực hiện chuyến đi

Tài xế cập nhật trạng thái chuyến:

```text
Đã nhận chuyến
      ↓
Đã đến điểm đón
      ↓
Đã đón khách
      ↓
Đang di chuyển
      ↓
Hoàn thành chuyến



# CAB System – Business Process

## 1. Mục đích nghiệp vụ

Mục đích của CAB System là tự động hóa và quản lý toàn bộ quy trình đặt xe:

- Khách hàng tạo yêu cầu đặt xe.
- Hệ thống tìm và phân công tài xế.
- Tài xế thực hiện chuyến đi.
- Hệ thống tính cước và thanh toán.
- Hệ thống gửi thông báo.
- Khách hàng đánh giá tài xế.
- Doanh nghiệp quản lý và báo cáo hoạt động.

---

## 2. Quy trình nghiệp vụ chính

```mermaid
flowchart TD
    A[Khách hàng] --> B[Đăng nhập hệ thống]
    B --> C[Nhập điểm đón và điểm đến]
    C --> D[Chọn loại xe]
    D --> E[Gửi yêu cầu đặt xe]
    E --> F[Hệ thống tiếp nhận yêu cầu]
    
    F --> G[Tìm tài xế phù hợp]
    G --> H{Có tài xế phù hợp?}
    
    H -- Không --> I[Thông báo không tìm được tài xế]
    H -- Có --> J[Gửi yêu cầu cho tài xế]
    
    J --> K{Tài xế nhận chuyến?}
    K -- Không --> G
    K -- Có --> L[Thông báo tài xế đã nhận chuyến]
    
    L --> M[Tài xế đến điểm đón]
    M --> N[Thông báo tài xế đã đến]
    N --> O[Tài xế đón khách]
    O --> P[Đang di chuyển]
    P --> Q[Hoàn thành chuyến]
    
    Q --> R[Tính cước]
    R --> S[Thanh toán]
    S --> T{Thanh toán thành công?}
    
    T -- Không --> U[Thông báo thanh toán thất bại]
    U --> V[Xử lý thanh toán lại]
    V --> S
    
    T -- Có --> W[Thông báo thanh toán thành công]
    W --> X[Khách hàng đánh giá tài xế]
    X --> Y[Lưu lịch sử chuyến đi]
```

---

# 3. Quy trình tìm và phân công tài xế

```mermaid
flowchart TD
    A[Yêu cầu đặt xe] --> B[Xác định tài xế phù hợp]
    B --> C[Kiểm tra vị trí]
    C --> D[Kiểm tra trạng thái sẵn sàng]
    D --> E[Kiểm tra tiêu chí vận hành]
    E --> F[Ưu tiên tài xế gần và phù hợp]
    F --> G[Gửi yêu cầu chuyến]
    
    G --> H{Tài xế phản hồi?}
    
    H -- Nhận --> I[Phân công tài xế]
    H -- Từ chối --> J[Tìm tài xế tiếp theo]
    H -- Không phản hồi --> J
    
    J --> K{Còn tài xế phù hợp?}
    K -- Có --> G
    K -- Không --> L[Thông báo không tìm được tài xế]
```

---

# 4. Quy trình thực hiện chuyến đi

```mermaid
stateDiagram-v2
    [*] --> Requested: Khách hàng đặt xe
    Requested --> Searching: Tìm tài xế
    Searching --> DriverAssigned: Tài xế nhận chuyến
    Searching --> Searching: Tài xế từ chối / không phản hồi
    Searching --> Cancelled: Không tìm được tài xế

    DriverAssigned --> DriverArriving: Tài xế di chuyển đến điểm đón
    DriverArriving --> Arrived: Tài xế đã đến
    Arrived --> PassengerPickedUp: Đã đón khách
    PassengerPickedUp --> InProgress: Đang di chuyển
    InProgress --> Completed: Hoàn thành chuyến
    Completed --> Payment: Tính cước và thanh toán
    Payment --> Finished: Thanh toán hoàn tất
    Finished --> [*]

    Cancelled --> [*]
```

---

# 5. Các nhóm chức năng hệ thống

```mermaid
mindmap
  root((CAB System))
    Customer Management
      Đăng ký
      Đăng nhập
      Cập nhật thông tin
      Lịch sử chuyến đi
      Đánh giá tài xế

    Booking Management
      Nhập điểm đón
      Nhập điểm đến
      Chọn loại xe
      Tạo yêu cầu đặt xe
      Theo dõi chuyến đi

    Driver Management
      Đăng ký tài xế
      Hồ sơ tài xế
      Thông tin phương tiện
      Trạng thái hoạt động
      Vị trí tài xế

    Driver Matching
      Tìm tài xế
      Kiểm tra vị trí
      Kiểm tra trạng thái
      Ưu tiên tài xế gần
      Xử lý từ chối
      Tìm tài xế tiếp theo

    Trip Management
      Nhận chuyến
      Đến điểm đón
      Đón khách
      Đang di chuyển
      Hoàn thành chuyến

    Payment
      Tính cước
      Tiền mặt
      Thanh toán điện tử
      Xử lý thanh toán thất bại

    Notification
      Thông báo khách hàng
      Thông báo tài xế
      Thông báo trạng thái chuyến
      Thông báo thanh toán

    Operations
      Quản lý khách hàng
      Quản lý tài xế
      Quản lý phương tiện
      Theo dõi chuyến
      Xử lý sự cố
      Tra cứu giao dịch

    Reporting
      Số lượng chuyến
      Doanh thu
      Tỷ lệ hoàn thành
      Tỷ lệ hủy
      Hiệu quả tài xế
```

---

# 6. Hệ thống cần đáp ứng

```mermaid
flowchart LR
    A((CAB System))

    A --> B[Functional Requirements]
    A --> C[Non-functional Requirements]

    B --> B1[Account Management]
    B --> B2[Booking Management]
    B --> B3[Driver Matching]
    B --> B4[Trip Management]
    B --> B5[Payment]
    B --> B6[Notification]
    B --> B7[Rating]
    B --> B8[Administration]
    B --> B9[Reporting]

    C --> C1[Scalability]
    C --> C2[Availability]
    C --> C3[Security]
    C --> C4[Performance]
    C --> C5[Maintainability]
    C --> C6[Extensibility]
    C --> C7[Auditability]
```

---

# 7. Mối quan hệ giữa nghiệp vụ và hệ thống

```mermaid
flowchart TD
    A[Business Objectives] --> B[Business Processes]
    
    B --> B1[Đặt xe]
    B --> B2[Tìm tài xế]
    B --> B3[Thực hiện chuyến]
    B --> B4[Tính cước]
    B --> B5[Thanh toán]
    B --> B6[Thông báo]
    B --> B7[Đánh giá]
    B --> B8[Quản lý vận hành]
    B --> B9[Báo cáo]

    B1 --> C[System Functions]
    B2 --> C
    B3 --> C
    B4 --> C
    B5 --> C
    B6 --> C
    B7 --> C
    B8 --> C
    B9 --> C

    C --> D[Scalability]
    C --> E[Security]
    C --> F[Availability]
    C --> G[Performance]
    C --> H[Extensibility]
```

## 8. Tóm tắt

```mermaid
flowchart LR
    A[Khách hàng] --> B[Đặt xe]
    B --> C[Tìm tài xế]
    C --> D[Phân công]
    D --> E[Thực hiện chuyến]
    E --> F[Tính cước]
    F --> G[Thanh toán]
    G --> H[Đánh giá]
    H --> I[Lịch sử]

    J[Nhân viên vận hành] --> K[Quản lý hệ thống]
    K --> B
    K --> C
    K --> E
    K --> G
    K --> I

    L[Ban giám đốc] --> M[Báo cáo]
    M --> K
```
