# BÁO CÁO THỰC HÀNH: TỔNG HỢP ACTIVITY & USE CASE DIAGRAM HỆ THỐNG RIKKEILOGISTICS

## 1. Mục tiêu và Bối cảnh
Tài liệu này là bản thuyết minh chi tiết cho bài thực hành mô hình hóa quy trình xử lý đơn hàng của RikkeiLogistics. Báo cáo cung cấp các bảng phân rã chức năng và phân tích quan hệ logic dưới góc nhìn của một Business Analyst.

---

## 2. PHẦN A — Phân tích Activity Diagram
Kịch bản nghiệp vụ: Khách hàng đặt đơn hàng. Hệ thống kiểm tra tồn kho tại Kho. Nếu Còn hàng, Bộ phận Kho thực hiện hai tác vụ song song: đóng gói đơn hàng và gửi thông báo xuất kho. Nếu Hết hàng, Bộ phận Kho báo hoàn tiền và kết thúc luồng nghiệp vụ.

| Loại Node | Tên Node / Tác vụ | Swimlane phụ trách |
| :--- | :--- | :--- |
| Initial Node | Bắt đầu | — |
| Action | Đặt đơn hàng | Khách hàng |
| Decision | Kiểm tra tồn kho (Còn hàng / Hết hàng) | Bộ phận Kho |
| Fork | **Tách nhánh đồng thời (khi Còn hàng)** | **Bộ phận Kho** |
| Action | **Đóng gói đơn hàng** | **Bộ phận Kho** |
| Action | **Gửi thông báo xuất kho** | **Bộ phận Kho** |
| Join | **Gộp nhánh đồng thời (sau khi xử lý xong)** | **Bộ phận Kho** |
| Action | **Báo hoàn tiền (nhánh Hết hàng)** | **Bộ phận Kho** |
| Final Node | Kết thúc | — |

---

## 3. PHẦN B — Phân tích Use Case Diagram
Hệ thống yêu cầu khách hàng phải đăng nhập (bắt buộc) trước khi Đặt đơn hàng. Khi đặt đơn, khách hàng có thể chọn yêu cầu Giao hàng hỏa tốc (tùy chọn). Chức năng đặt đơn hàng được chuyên biệt hóa thành hai dạng: Đặt đơn hàng lẻ và Đặt đơn hàng sỉ.

| Use Case A | Use Case B | Quan hệ | Giải thích logic |
| :--- | :--- | :--- | :--- |
| Đặt đơn hàng | Đăng nhập | `<<include>>` | Phải đăng nhập trước khi đặt đơn hàng (Bắt buộc). |
| Đặt đơn hàng | Giao hàng hoả tốc | `<<extend>>` | **Tính năng giao hàng hỏa tốc là tùy chọn, khách hàng có thể yêu cầu thêm khi đặt đơn.** |
| Đặt đơn hàng | Đặt đơn hàng lẻ | `<<generalization>>` | Là một dạng chuyên biệt của Đặt đơn hàng (Kế thừa). |
| Đặt đơn hàng | **Đặt đơn hàng sỉ** | `<<generalization>>` | **Là một dạng chuyên biệt của Đặt đơn hàng (Kế thừa, dành cho số lượng lớn).** |

---
*Ghi chú: Sinh viên đính kèm file này cùng với hình ảnh xuất từ draw.io để nộp bài.*
