- Công cụ thay thế NPM

# Đặc trưng
- **Tốc độ**: yarn sẽ tạo cache cho tất cả gói đã được tải về, và tải đồng thời nhiều gói cùng lúc nên tốc độ download rất nhanh
- **Tin cậy**: Sử dụng tập tin lock với formant chi tiết nhưng ngắn gọn đảm bảo tính nhất quán khi cài đặt các gói giữa các hệ thống (máy dev và máy chủ)
- **Bảo mật**: Sử dụng checksum để đảm bảo tính nguyên vẹn của code trước khi thực thi

# Tính năng

- offline mode: khi đã tải về, yarn sẽ cache lại và khi có thể cài đặt mà không cần internet
- Deterministic: các gói thư viện sẽ được cài đặt nhất quán cho dù thứ tự cài đặt khác nhau đối với các máy
- Network Performance: sử dụng hiệu quả hàng đợi các request và tránh waterfall các request để tối ưu tốc độ sử dụng mạng
- Multiple Registries: Cài đặt các gói từ các registries như Bower hay NPM đều đảm bảo workflow giống nhau
- Network Resilience: Nếu một request bị fail thì nó không làm cho tiến trình bị dừng lại, khác npm là nếu npm bị lỗi thì bị dừng, ngoài ra nó còn cố gắng thử lại
- Flat Mode: Giải quyết việc không đồng nhất phiên bản của các gói thành một gói để tránh trùng lặp

# Cài đặt

```cmd
npm install -g yarn
```

# Tổng hợp các lệnh

- Tạo dự án mới

```cmd
yarn init
```

- Thêm các thư viện

```cmd
yarn add [package]
yarn add [package]@[version]
yarn add [package]@[tag]
```

-  Cập nhật thư viện

```cmd
yarn upgrade [package]
yarn upgrade [package]@[version]
yarn upgrade [package]@[tag]
```

Xóa

```cmd
yarn remove [package]
```

Cài đặt tất cả các gói
```cmd
yarn
yarn install
```

Kiểm tra các gói phụ thuộc: Kiểm tra tính toàn vẹn của tất cả các gói:
```cmd
yarn check
```

- Yarn tự động tạo file `yarn.lock` khi cài đặt hoặc cập nhật gói. File này giúp đảm bảo các lần cài đặt sau đều sử dụng đúng phiên bản của gói, tránh lỗi không tương thích giữa các phiên bản
Note
Do YARN cũng sử dụng package.json nên nếu dự án đã có thì việc sử dụng YARN cũng không khác mấy, chỉ cần bạn xóa tất cả các thư mục trong node_modules, sau đó dùng yarn để cài lại.


@@ NPM
Đối với npm việc cập nhật thư viện sẽ thông qua
```cmd
npm update <package_name>
```

Cập nhật phiên bản cụ thể

```cmd
npm install <package_name>@<version>
```

example: npm install express@4.17.1

Cập nhật toàn bộ gói
```cmd
npm update
```

Kiểm tra các gói có phiên bản nào mới không
```cmd
ncu
```

Cập nhật các gói lên phiên bản mới

```cmd
ncu -u
```

Lệnh này sẽ cập nhật các phiên bản trong `package.json`, sau đó bạn có thể chạy: `bash npm install` để cài đặt các phiên bản mới nhất.

Cập nhật phiên bản mới nhất của npm

```cmd
npm install -g npm
```
