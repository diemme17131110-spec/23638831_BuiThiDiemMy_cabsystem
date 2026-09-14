<div align="center">

# 🚖 CAB System

### Online Ride Booking Platform

**Business Analysis Project – Industrial University of Ho Chi Minh City**

![Status](https://img.shields.io/badge/Status-In%20Development-blue)
![MVP](https://img.shields.io/badge/MVP-7%20Weeks-success)
![Documentation](https://img.shields.io/badge/Documentation-Complete-brightgreen)

</div>

---

## 📖 Overview

CAB System là nền tảng đặt xe trực tuyến nhằm tự động hóa toàn bộ quy trình từ khi khách hàng tạo yêu cầu đặt xe đến khi chuyến đi hoàn thành, thanh toán và đánh giá tài xế.

### Mục tiêu

- Tự động tìm và phân công tài xế.
- Theo dõi chuyến đi theo thời gian thực.
- Hỗ trợ thanh toán tiền mặt và điện tử.
- Quản lý tập trung khách hàng, tài xế và chuyến đi.
- Khả năng mở rộng trong tương lai.

---

## 📑 Table of Contents

- Stakeholder Analysis
- Business Process
- Business Requirements
- Functional Requirements
- Use Case
- Business Rules
- Testing
- Roadmap

---

# 👥 Stakeholders

| Stakeholder | Vai trò |
|-------------|----------|
| Management | Định hướng dự án |
| Customer | Đặt xe |
| Driver | Thực hiện chuyến |
| Operations Staff | Quản lý vận hành |
| Administrator | Quản trị hệ thống |

---

# 📊 Stakeholder Matrix

```mermaid
quadrantChart
    title CAB System Stakeholder Matrix
    x-axis Low Interest --> High Interest
    y-axis Low Power --> High Power

    quadrant-1 Manage Closely
    quadrant-2 Keep Satisfied
    quadrant-3 Monitor
    quadrant-4 Keep Informed

    "Management":[0.9,0.95]
    "Customer":[0.95,0.6]
    "Driver":[0.9,0.6]
    "Operations":[0.9,0.8]
```

---

# 🔄 Business Process

```mermaid
flowchart TD
    Customer --> Booking
    Booking --> Matching
    Matching --> Driver
    Driver --> Trip
    Trip --> Payment
    Payment --> Rating
```

---

# 🚀 MVP Scope

| Module | Status |
|---------|--------|
| Account | ✅ |
| Booking | ✅ |
| Driver Matching | ✅ |
| Trip | ✅ |
| Payment | ✅ |
| Notification | ✅ |
| Operations | ✅ |

---

# 📚 Documentation

| Document | Location |
|----------|----------|
| Stakeholder Analysis | docs/requirements/stakeholder_analysis.md |
| Business Requirements | docs/requirements/business_requirements.md |
| Functional Requirements | docs/requirements/functional_requirements.md |
| Business Rules | docs/requirements/business_rules.md |
| Business Process | docs/design/business_process.md |
| Use Case Diagram | docs/design/usecase_diagram.md |
| Use Case Specification | docs/design/usecase_specification.md |
| Test Cases | docs/testing/test_case.md |

---

# 📅 Roadmap

| Week | Module |
|------|--------|
| 1 | Account |
| 2 | Driver |
| 3 | Booking |
| 4 | Matching |
| 5 | Payment |
| 6 | Notification |
| 7 | Testing |

---
# Quy trình nghiệp vụ – CAB System

> Tài liệu mô tả quy trình nghiệp vụ của hệ thống CAB, từ quy trình hiện tại đến quy trình đề xuất cho phiên bản MVP 7 tuần.

---

## Mục lục

- Mục tiêu nghiệp vụ
- Quy trình hiện tại (AS-IS)
- Quy trình đề xuất (TO-BE)
- Quy trình đặt xe
- Quy trình tìm và phân công tài xế
- Trạng thái chuyến đi
- Nhóm chức năng của hệ thống
- So sánh AS-IS và TO-BE
- Tóm tắt

---

# 1. Mục tiêu nghiệp vụ

Hệ thống **CAB System** được xây dựng nhằm tự động hóa toàn bộ quy trình đặt xe, từ khi khách hàng tạo yêu cầu đến khi chuyến đi hoàn thành.

### Mục tiêu chính

- Giảm việc phân công tài xế thủ công.
- Rút ngắn thời gian xử lý yêu cầu.
- Giúp khách hàng theo dõi chuyến đi dễ dàng.
- Quản lý tập trung khách hàng, tài xế và chuyến đi.
- Hỗ trợ thanh toán và thông báo.
- Dễ mở rộng trong tương lai.

---

# 2. Quy trình hiện tại (AS-IS)

Hiện nay quy trình còn phụ thuộc nhiều vào nhân viên vận hành.

```mermaid
flowchart TD
    A[Khách hàng cần đặt xe]
    B[Liên hệ tổng đài]
    C[Nhân viên tiếp nhận]
    D[Tìm tài xế thủ công]
    E[Phân công tài xế]
    F[Tài xế thực hiện chuyến]
    G[Khách hàng thanh toán]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
```

## Hạn chế

| Vấn đề | Ảnh hưởng |
|---------|-----------|
| Tìm tài xế thủ công | Mất thời gian |
| Khó theo dõi chuyến | Khách hàng thiếu thông tin |
| Quản lý giao dịch rời rạc | Khó kiểm soát |
| Phụ thuộc nhân viên | Chi phí vận hành cao |
| Khó mở rộng | Không đáp ứng khi số lượng người dùng tăng |

---

# 3. Quy trình đề xuất (TO-BE)

Hệ thống sẽ tự động xử lý phần lớn các bước.

```mermaid
flowchart TD
    A[Khách hàng]
    B[Đặt xe]
    C[Hệ thống nhận yêu cầu]
    D[Tìm tài xế]
    E{Có tài xế?}
    F[Gửi yêu cầu cho tài xế]
    G{Tài xế nhận?}
    H[Phân công tài xế]
    I[Thực hiện chuyến]
    J[Tính cước]
    K[Thanh toán]
    L[Đánh giá]
    M[Lưu lịch sử]

    A --> B
    B --> C
    C --> D
    D --> E

    E -- Không --> N[Thông báo không có tài xế]

    E -- Có --> F
    F --> G

    G -- Không --> D
    G -- Có --> H

    H --> I
    I --> J
    J --> K
    K --> L
    L --> M
```

### Điểm cải tiến

- Tự động tìm tài xế.
- Tự động phân công.
- Theo dõi chuyến theo thời gian thực.
- Quản lý thanh toán tập trung.

---

# 4. Quy trình đặt xe

```mermaid
flowchart TD
    A[Khách hàng mở ứng dụng]
    B[Nhập điểm đón]
    C[Nhập điểm đến]
    D[Chọn loại xe]
    E[Xác nhận đặt xe]
    F[Hệ thống tạo yêu cầu]
    G[Chuyển sang trạng thái Đang tìm tài xế]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
```

### Kết quả mong đợi

- Yêu cầu được tạo thành công.
- Hệ thống bắt đầu tìm tài xế.
- Khách hàng nhận được thông báo.

---

# 5. Quy trình tìm và phân công tài xế

Đây là quy trình quan trọng nhất của hệ thống.

```mermaid
flowchart TD
    A[Yêu cầu đặt xe]
    B[Tìm tài xế phù hợp]
    C[Kiểm tra vị trí]
    D[Kiểm tra trạng thái]
    E[Ưu tiên tài xế gần]
    F[Gửi yêu cầu]

    G{Tài xế phản hồi?}

    H[Nhận chuyến]
    I[Từ chối]
    J[Không phản hồi]

    K[Tìm tài xế tiếp theo]
    L[Thông báo không có tài xế]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G

    G -- Nhận --> H
    G -- Từ chối --> I
    G -- Không phản hồi --> J

    I --> K
    J --> K

    K --> B

    B --> L
```

### Quy tắc xử lý

- Chỉ tài xế đang sẵn sàng mới được nhận chuyến.
- Nếu tài xế từ chối, hệ thống tìm người khác.
- Nếu tài xế không phản hồi, hệ thống tiếp tục tìm.
- Nếu không còn tài xế phù hợp, khách hàng được thông báo.

---

# 6. Trạng thái chuyến đi

Mỗi chuyến đi sẽ thay đổi trạng thái theo từng bước.

```mermaid
stateDiagram-v2
    [*] --> DangTimTaiXe

    DangTimTaiXe --> DaPhanCong: Tài xế nhận
    DangTimTaiXe --> Huy: Không có tài xế

    DaPhanCong --> DangDenDiemDon
    DangDenDiemDon --> DaDen
    DaDen --> DaDonKhach
    DaDonKhach --> DangDiChuyen
    DangDiChuyen --> HoanThanh

    HoanThanh --> ThanhToan
    ThanhToan --> KetThuc

    KetThuc --> [*]
    Huy --> [*]
```

### Ý nghĩa từng trạng thái

| Trạng thái | Mô tả |
|------------|------|
| Đang tìm tài xế | Hệ thống đang tìm người phù hợp |
| Đã phân công | Có tài xế nhận chuyến |
| Đang đến điểm đón | Tài xế đang di chuyển |
| Đã đến | Tài xế đến nơi |
| Đã đón khách | Bắt đầu chuyến đi |
| Đang di chuyển | Chuyến đang diễn ra |
| Hoàn thành | Kết thúc chuyến |
| Thanh toán | Xử lý giao dịch |
| Kết thúc | Hoàn tất |

---

# 7. Nhóm chức năng của hệ thống

```mermaid
mindmap
  root((CAB System))
    Quản lý tài khoản
      Đăng ký
      Đăng nhập
      Cập nhật thông tin

    Đặt xe
      Điểm đón
      Điểm đến
      Loại xe

    Tìm tài xế
      Kiểm tra vị trí
      Kiểm tra trạng thái
      Phân công

    Quản lý chuyến
      Đến điểm đón
      Đón khách
      Hoàn thành

    Thanh toán
      Tiền mặt
      Điện tử

    Thông báo

    Quản lý vận hành
```

---

# 8. So sánh quy trình hiện tại và quy trình đề xuất

| Quy trình hiện tại | Quy trình đề xuất |
|-------------------|------------------|
| Gọi tổng đài | Đặt xe trên hệ thống |
| Tìm tài xế thủ công | Tự động tìm tài xế |
| Khó theo dõi | Theo dõi thời gian thực |
| Phân công thủ công | Tự động phân công |
| Thanh toán rời rạc | Quản lý tập trung |
| Khó mở rộng | Dễ mở rộng |

---

# 9. Mối liên hệ giữa nghiệp vụ và hệ thống

```mermaid
flowchart TD
    A[Mục tiêu nghiệp vụ]
    B[Quy trình đặt xe]
    C[Tìm tài xế]
    D[Thực hiện chuyến]
    E[Thanh toán]
    F[Thông báo]
    G[Báo cáo]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
```

---

# 10. Tóm tắt

Phiên bản MVP tập trung vào quy trình cốt lõi:

```text
Đặt xe
   ↓
Tìm tài xế
   ↓
Phân công
   ↓
Thực hiện chuyến
   ↓
Tính cước
   ↓
Thanh toán
   ↓
Đánh giá
```

Quy trình này giúp giảm thao tác thủ công, tăng tốc độ xử lý và tạo nền tảng để mở rộng hệ thống trong tương lai.

# 👨‍💻 Student

**Bùi Thị Diễm My**

Industrial University of Ho Chi Minh City
