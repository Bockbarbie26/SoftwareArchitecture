# SoftwareArchitecture
# ADR-001: Tách hệ thống Monolithic thành Microservices

**Status:** Accepted  
**Date:** 13-04-2025  
**Author:** DevBluprint Architecture Designer

---

## Context

Hệ thống hiện tại được xây dựng dưới dạng monolithic. Khi có yêu cầu cập nhật hoặc sửa lỗi nhỏ, toàn bộ hệ thống phải được build và deploy lại. Điều này gây mất thời gian, tốn tài nguyên và tăng nguy cơ lỗi khi hệ thống ngày càng mở rộng. CTO yêu cầu nhóm kiến trúc sư xem xét giải pháp cải thiện khả năng mở rộng, triển khai và bảo trì hệ thống.

---

## Decision

Chuyển kiến trúc hệ thống từ **Monolithic** sang **Microservices**.

---

## Justification

### 🔧 Lý do kỹ thuật (Technical Justification)

- Giảm coupling giữa các module, giúp phát triển và triển khai độc lập. Monolith thường chứa quá nhiều logic trong một codebase, gây khó khăn trong việc hiểu, phát triển và bảo trì. Với microservices, mỗi service chỉ đảm nhiệm một chức năng rõ ràng, giúp dễ quản lý hơn.

- Công nghệ linh hoạt, cho phép sử dụng ngôn ngữ, framework khác nhau phù hợp với từng service. (Java cho core logic, Python cho ML, Node.js cho APIs...)

- Microservices giúp scale những service có tải cao (như service đặt hàng hoặc tìm tài xế) mà không cần scale cả hệ thống.

- Cho phép triển khai riêng từng phần, giảm downtime, tăng tốc độ triển khai và dễ quản lý.

### 💼 Lý do kinh doanh (Business Justification)

- Tăng tốc độ đưa tính năng mới ra thị trường, release nhanh từng chức năng nhỏ mà không phải chờ team khác. Điều này cực kỳ quan trọng trong thị trường cạnh tranh như giao đồ ăn.

- Tăng độ tin cậy: lỗi ở 1 service không làm gián đoạn toàn hệ thống. Giảm chi phí sửa lỗi và bảo trì hệ thống.

- Hỗ trợ tốt cho mô hình DevOps và phát triển theo mô hình tổ chức linh hoạt (Scrum team,...)

---

## Consequences

### ✅ Tích cực

- Dễ bảo trì, dễ mở rộng, triển khai nhanh.
- Tăng độ ổn định của hệ thống và dễ bảo trì.

### ❌ Tiêu cực

- Tăng độ phức tạp: cần thêm công cụ quản lý, theo dõi, giao tiếp giữa service.
- Cần áp dụng tốt CI/CD và DevOps .

---

## Alternatives

- **Giữ nguyên kiến trúc monolithic:**  
  Không giải quyết được vấn đề scale độc lập và triển khai.

- **Chuyển sang modular monolith:**  
  Dễ triển khai hơn microservices nhưng vẫn bị giới hạn về scale và triển khai độc lập.

