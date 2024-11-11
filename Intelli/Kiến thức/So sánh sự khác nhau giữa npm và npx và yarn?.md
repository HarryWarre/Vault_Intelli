# NPM 
- bộ quản lý package của NodeJS
- Quản lý phiên bản: ghi lại các gói và phiên bản trong package.json và giữa cho dự án đồng nhất về môi trường
- Quản lý script: Các lệnh được định nghĩa trong package.json có thể chạy bằng cách sử dụng `npm run <script name>`

Ưu điểm
- Tích hợp chặt chẽ với Node.s và cài đặt mặc định với Node
- Cung cấp lệnh `npm audit` để kiểm tra các lỗ hổng bảo mật trong các gói

Nhược điểm:
- Một số tính năng nâng cao (như hỗ trợ monorepo) cần công cụ khác như ([[lerna]])
- Đôi khi có thể chậm hơn Yarn trong một số tình huống
____

# npx (Node Package Excecute) 
- Công cụ đi kèm của npm phiên bản 5.2 trở lên
- Chạy các lệnh của gói mà không cần cài đặt. Bạn có thể chạy một công cụ trực tiếp mà không cần phải cài đặt
- Chạy phiên bản cụ thể của một gói: Sử dụng một phiên bản cụ thể của một công cụ

Ưu điểm: 
- Không cần cài đặt lâu dài: Hữu ích để chạy các công cụ tạm thời mà không tác dụng lên môi trường cài đặt gói
- Tiết kiệm không gina: Không cần cìa đặt vào dự án, giảm tải không gian bộ nhớ
- Dễ thử nghiệm: Cho phép chạy thử các phiên bản khác nhau mà không cần phải thay đổi phiên bản chính thức trong dự án

Nhược điểm:
- Kém hiệu quả với các lệnh cần chạy thường xuyên: Do khoongn lưu trữ cố định, npx sẽ tải lại các gói mỗi khi chạy
___
# Yarn
- Là trình quản lý gói do Facebook phát triển như một giải pháp thay thế cho npm, với các tính năng nâng cao:
	- Cài đặt gói nhanh hơn: Yarn sử dụng cache -> Giảm thời gian cài đặt gói
	- Quản lý phiên bản đồng nhất: tạo file yarn.lock để đảm bảo các lần cài đặt đều đúng phiên bản 
	- Hỗ trợ monorepo: Tính năng Workspaces của Yarn giúp dễ dàng quản lý các dự án lớn chứa nhiều gói con (monorepo) trong cùng một kho lưu trữ

Ưu điểm
- Nhanh hơn npm trong nhiều trường hợp: cache mạnh giúp cài đặt lại các gói nhanh chóng.
- Workspaces: Hữu ích cho các dự án monorepo lớn
- Giao diện thân thiện: đẹp :>

Nhược điểm
- Không phải công cụ mặc định của Node.js
- Sự tương thích không hoàn toàn với npm: Dù hầu hết các gói đều hỗ trợ Yarn, nhưng một số tính năng có thể khác biệt

___
### **So sánh tổng thể**

| Công cụ  | Ưu điểm                                                        | Nhược điểm                                                  | Dùng trong tình huống                                      |
| -------- | -------------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------- |
| **npm**  | Tích hợp với Node.js, dễ sử dụng, hỗ trợ bảo mật (`npm audit`) | Có thể chậm hơn Yarn, thiếu tính năng nâng cao như monorepo | Quản lý gói cơ bản và các dự án nhỏ đến trung bình         |
| **npx**  | Chạy lệnh trực tiếp mà không cần cài đặt, tiết kiệm không gian | Không tối ưu cho các lệnh cần chạy thường xuyên             | Chạy các công cụ CLI một lần hoặc kiểm thử công cụ mới     |
| **Yarn** | Cài đặt nhanh, có cache mạnh, hỗ trợ monorepo tốt              | Cần cài đặt bổ sung, không phải công cụ mặc định            | Các dự án lớn, monorepo, hoặc nơi cần tốc độ cài đặt nhanh |

