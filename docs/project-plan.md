# KẾ HOẠCH DỰ ÁN

## 1. Các chức năng dự kiến của trang web
- Chức năng giỏ hàng
- Chức năng tìm kiểm sản phẩm
- Chức năng thanh toán
- Chức năng giới thiệu các điểm đến và đặc sản của Tây Nguyên
- Chức năng xem chi tiết thông tin sản phẩm

## 2. Kế hoạch phát triển chức năng thanh toán
Nhằm nâng cấp website từ nền tảng giới thiệu thông tin thành một hệ thống thương mại điện tử hoàn chỉnh, dự án định hướng xây dựng và phát triển chức năng Đặt hàng theo 3 giai đoạn chính:

### 1. Quản lý Giỏ hàng & Luồng Đặt hàng Cơ bản (Client-side)
* **Lưu trữ Giỏ hàng:** Sử dụng `localStorage` của trình duyệt để lưu giữ danh sách sản phẩm và số lượng, đảm bảo không bị mất dữ liệu khi người dùng chuyển trang hoặc làm mới trình duyệt.
* **Quy trình Đặt hàng:** Xây dựng form thu thập thông tin giao hàng *(Họ tên, Số điện thoại, Địa chỉ nhận hàng, Ghi chú)* và tự động tính tổng hóa đơn tạm tính trước khi xác nhận đơn.

### 2. Tích hợp Thanh toán & Tự động hóa Giao dịch
* **Đa dạng Phương thức Thanh toán:** Hỗ trợ thanh toán khi nhận hàng (COD) và tích hợp API thanh toán chuyển khoản nhanh qua mã một số ví điện tử qua QR hiện nay như **VietQR**, **VNPay** *(tự động điền đúng Số tiền và Nội dung chuyển khoản là Mã đơn hàng)*.
* **Xác thực Dữ liệu (Validation):** Áp dụng Client-side Validation (Regex) để kiểm tra tính chính xác của Số điện thoại, Địa chỉ giao hàng nhằm giảm thiểu đơn hàng ảo.

### 3. Quản lý Đơn hàng & Tích hợp Backend (Định hướng mở rộng)
* **Xử lý Đơn hàng (Order Management):** Chuyển đổi mô hình lưu trữ từ `localStorage` sang gửi dữ liệu qua **RESTful API** về cơ sở dữ liệu trung tâm (Database).
* **Trạng thái Đơn hàng:** Xây dựng giao diện Quản trị viên (Admin Dashboard) cho phép quản lý vòng đời đơn hàng qua các trạng thái: `Mới đặt (Pending)` ➔ `Đã xác nhận (Confirmed)` ➔ `Đang giao (Shipping)` ➔ `Hoàn thành (Completed)`.
* **Thông báo tự động:** Phát triển tính năng gửi email xác nhận đơn hàng tự động cho khách hàng ngay khi đặt hàng thành công.