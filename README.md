# SoftwareArchitecture
# ADR-001: Tách hệ thống Monolithic thành Microservices

**Status:** Accepted  
**Date:** 2025-04-14  
**Author:** [Tên bạn]

---

## Context

Hệ thống hiện tại được xây dựng dưới dạng monolithic. Khi có yêu cầu cập nhật hoặc sửa lỗi nhỏ, toàn bộ hệ thống phải được build và deploy lại. Điều này gây mất thời gian, tốn tài nguyên và tăng nguy cơ lỗi khi hệ thống ngày càng mở rộng. CTO yêu cầu nhóm kiến trúc sư xem xét giải pháp cải thiện khả năng mở rộng, triển khai và bảo trì hệ thống.

---

## Decision

Chuyển kiến trúc hệ thống từ monolithic sang microservices.

---

## Justification

### 🔧 Lý do kỹ thuật (Technical Justification)

- **Tách biệt trách nhiệm (Separation of Concerns):**  
  Mỗi service đảm nhận một chức năng riêng biệt, giúp dễ quản lý, bảo trì và phát triển.

- **Triển khai độc lập (Independent Deployment):**  
  Mỗi service có thể được triển khai riêng biệt, giảm thời gian build/deploy và giảm rủi ro.

- **Mở rộng theo chiều ngang (Horizontal Scalability):**  
  Chỉ những service có nhu cầu cao mới cần scale, tiết kiệm tài nguyên.

- **Công nghệ linh hoạt (Polyglot Tech Stack):**  
  Cho phép sử dụng ngôn ngữ hoặc framework phù hợp nhất cho từng service.

- **Độ ổn định cao hơn:**  
  Lỗi ở một service không ảnh hưởng toàn bộ hệ thống.

### 💼 Lý do kinh doanh (Business Justification)

- **Tăng tốc độ đưa sản phẩm ra thị trường (Time-to-Market):**  
  Các nhóm có thể phát triển và triển khai nhanh các tính năng nhỏ.

- **Dễ mở rộng nhóm phát triển:**  
  Cho phép tổ chức thành nhiều nhóm nhỏ làm việc song song hiệu quả hơn.

- **Giảm thiểu rủi ro triển khai:**  
  Một lỗi khi deploy chỉ ảnh hưởng một phần hệ thống.

- **Tối ưu chi phí vận hành:**  
  Scale theo nhu cầu thực tế giúp tiết kiệm tài nguyên.

---

## Consequences

### ✅ Tích cực

- Dễ bảo trì, dễ mở rộng, triển khai nhanh.
- Tăng độ ổn định của hệ thống.
- Hỗ trợ phát triển nhanh và phân tán.

### ❌ Tiêu cực

- Tăng độ phức tạp: cần thêm công cụ quản lý, theo dõi, giao tiếp giữa service.
- Yêu cầu CI/CD mạnh và kinh nghiệm DevOps.

---

## Alternatives

- **Giữ nguyên kiến trúc monolithic:**  
  Không giải quyết được vấn đề về mở rộng và triển khai.

- **Chuyển sang modular monolith:**  
  Dễ triển khai hơn microservices nhưng vẫn bị giới hạn về scale và triển khai độc lập.

