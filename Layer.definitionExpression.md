# Giới thiệu

- Là một thuộc tính được sử dụng để lọc các đối tượng hiển thị trong một lớp bản đồ (layer) dựa trên các tiêu chí cụ thể.
- Nó hoạt động giống nhau như một câu truy vấn SQL, cho phép chỉ định điều kiện để giới hạn các đối tượng sẽ được hiển thị từ lớp dữ liệu

# Các hoạt động 

- `definitionExpression` xác định một chuỗi điều kiện (SQL WHERE clause) mà các đối tượng trong layer phải đáp ứng để được hiển thị trên bản đồ

- Các đối tượng không thỏa mã điều kiện này sẽ bị ẩn, nhwung vẫn tồn tại trong cơ sở dữ liệu
## Ví dụ

- Có một lớp chứa dữ liệu về các tòa nhà, bạn muốn hiển thị chỉ những tòa nahf có chiều cao lớn hơn 100:
```js
layer.definitionExpression = "height > 100"
```

## Sử dụng
- Mapview và SceneView: Khi sử dụng MapView hoặc SceneView, `definitionExpression` sẽ tự động áp dụng để lọc đối tượng hiển thị trong view
- FeatureLayerL: Một cách phổ biến sử dụng `definitionExpression` là với `FeatureLayer`, nơi nó giúp bạn tập trung vào các đối tượng có ý nghĩa cho ứng dụng 

## Lợi ích
- Giúp tăng hiệu suất ứng dụng bằng cách chỉ tải và hiển thị các ứng dụng cần thiết
- Cho phép người dùng làm việc với một tập hợp dữ liệu nhỏ hơn, dễ dàng quản lý hơn

### note:
`definitionExpression` chỉ tác động đến việc hiển thị, không xóa hoặc thay đổi dữ liệu thực tế trong lớp

