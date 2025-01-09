# Local Storage
- Khả năng lưu trữ vô hạn. Chỉ bị xóa bằng Javascript hoặc bằng bộ nhớ trình duyệt hay localstorage API
- Lưu trữ được 5MB, cho phép bạn lưu trữ thông tin tương đối lớn lên đến 5MB, lưu được lượng thông tin lớn nhất trong 3 loại.
- Không gửi thông tin lên server như Cookie nên bảo mật tốt hơn
# Session Storage
- Lưu trên Client: Cũng giống như localStorage thì sessionStorage cũng dùng để lưu trữ dữ liệu trên trình duyệt của khách truy cập (client).
- Mất dữ liệu khi đóng tab: Dữ liệu của sessionStorage sẽ mất khi bạn đóng trình duyệt.
- Dữ liệu không được gửi lên Server
- Thông tin lưu trữ nhiều hơn cookie (ít nhất 5MB)
# Cookie
- Thông tin được gửi lên server: Cookie sẽ được truyền từ server tới browser và được lưu trữ trên máy tính của bạn khi bạn truy cập vào ứng dụng
- Cookie chủ yếu là để đọc phía máy chủ (cũng có thể được đọc ở phía máy khách), localStorage và sessionStorage chỉ có thể được đọc ở phía máy khách
- Có thời gian sống: Mỗi cookie thường có khoảng thời gian timeout nhất định do lập trình viên xác định trước.
- Lưu trữ: cho phép lưu trữ tối đa 4KB và vài chục cookie cho một domain.