Là một công cụ mạnh mẽ quản lý các dự án *monorepo*, nơi có nhiều gói package cùng tồn tại trong một kho lưu trữ (repository). 
Monorepo thường được sử dụng cho các dự án lớn khi bạn muốn quản lý nhiều thư viện hoặc dự án con trong cùng một repo, giúp tăng cường tính liên kết và chia sẻ mã dễ dàng.

```bash
 npm install -g lerna
```

hoặc cài vào dự án

```bash
npm install --save-dev lerna
```

# Khởi tạo dự án với lerna

Sau khi cài đặt, có thể tạo một monorepo với Lerna

```bash
lerna init
```

Sẽ tạo một cấu trúc thư mục :
- `lerna.json`: File cấu hình cho Lerna
- `packages/`: Thư mục chứa các gói con (sub-packages) của dự án

Thêm gói vào monorepo
Trong monorepo, bạn có thể thêm các gói vào thư mục packages, Ví dụ tạo một thư mục cho một gói mới

```bash
mkdir packages/my-package
cd packages/my-package
npm init -y
```

Hoặc Lerna hỗ trợ lệnh để tự động tạo một gói mới:

```bash
lerna create <package-name>
```

### **Cài đặt phụ thuộc và Liên kết gói**

Lerna hỗ trợ quản lý phụ thuộc giữa các gói nội bộ với nhau. Để cài đặt tất cả các phụ thuộc và liên kết gói trong monorepo, bạn có thể chạy:

```bash
lerna bootstrap
```

Lệnh này sẽ:

- Cài đặt tất cả các phụ thuộc cần thiết cho từng gói.
- Tạo liên kết `symlink` giữa các gói trong monorepo để gói này có thể sử dụng các gói nội bộ khác mà không cần đăng lên npm.

### **Chạy Lệnh trên Tất cả Gói**

Lerna giúp bạn chạy các lệnh trên tất cả các gói con. Ví dụ, nếu bạn muốn chạy script `build` trên tất cả các gói:

```
lerna run build
```

**Lệnh phổ biến**:

- `lerna run test`: Chạy script `test` trên tất cả các gói.
- `lerna run lint`: Chạy lệnh kiểm tra mã (lint) trên tất cả các gói.

### **Quản lý Phiên bản và Phát hành**

Lerna cung cấp công cụ quản lý phiên bản rất mạnh, giúp tự động cập nhật phiên bản cho các gói khi bạn chuẩn bị phát hành.

- **Phiên bản đồng bộ** (`fixed versioning`): Tất cả các gói có cùng một phiên bản. Khi cập nhật, tất cả đều được tăng phiên bản cùng lúc.
- **Phiên bản độc lập** (`independent versioning`): Các gói có thể có phiên bản khác nhau, và chỉ các gói có thay đổi mới được tăng phiên bản.

Để phát hành các gói với Lerna, bạn có thể dùng lệnh:

```bash
lerna publish
```

### **Lựa chọn Kiến trúc Dự án với Lerna**

- **Monorepo với Nhiều gói**: Nếu bạn có nhiều thư viện phụ thuộc lẫn nhau, bạn có thể cấu trúc theo kiểu monorepo với mỗi thư viện trong thư mục `packages/`.
- **Sử dụng Kết hợp với Yarn Workspaces**: Lerna kết hợp tốt với Yarn Workspaces, giúp quản lý tốt hơn việc chia sẻ và cài đặt các gói phụ thuộc.

### **Các Lệnh và Tùy chọn Khác**

- **`lerna add <package>`**: Thêm một gói phụ thuộc vào tất cả các gói hoặc một gói con cụ thể.
- **`lerna clean`**: Xóa thư mục `node_modules` trong tất cả các gói.
- **`lerna exec -- <command>`**: Chạy lệnh shell tùy chỉnh trên từng gói.