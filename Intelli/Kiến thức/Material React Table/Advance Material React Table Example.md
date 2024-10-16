Tags: #muiReactTable #tables #react #mui 

Reference: [Advance Table Example](https://www.material-react-table.com/docs/examples/advanced)
Version: 3.0.1
# Introduce
- Trong phần advance material React table, ngoài các phần props mặc định được bật lên, có những phần props hoặc các phần custom có thể thêm khi sử dụng thư viện Material React Table

# Example
Trong phần advance, có 2 phần chính có thể custom: 
- Column
	- Custom cell đối với từng cột xác định
- Table
	- Enable các props đặc biệt
	- Điều chỉnh Displaymode
	- custom style của các element có trong MRT
# Giải thích 
```js
enableColumnFilterModes: true,
```
Phần này khi enable sẽ cho phép các cột có thể filter

```js
enableColumnOrdering: true,
```

Phần này khi enable sẽ cho phép người dùng có thể tùy biến sắp xếp các cột trong MRT

`enableGrouping`: ch phép nhóm các hàng dữ liệu lại dựa trên giá trị của một hoặc nhiều cột. Điều này hữu ích khi bạn muốn tổng hợp và phân tích dữ liệu theo các nhóm cụ thể

`enable ColumnPining`: Cho phép bạn cố định các cột ở bên trái hoặc bên phải của bảng, giúp chúng luôn hiển thị ngay cả khi cuộn ngang

`enableFacetedValues`: Tạo ra một giao diện lọc dữ liệu dựa trên các giá trị của từng cột. Ví dụ, nếu bạn có một cột "Quốc gia", bạn có thể tạo một bộ lọc để chỉ hiển thị các hàng có quốc gia bạn muốn

`enableRowActions`: Cho phép bạn thêm các hành động tùy chỉnh vào từng hàng, như chỉnh sửa, xóa hoặc xem chi tiết

`enableRowSelection`: Cho phép bạn chọn nhiều hàng cùng một lúc để thực hiện các hành động trên nhiều hàng

`initialState`
	`showColumnFilters` Hiển thị bộ lọc cột cho phép người dùng lọc dữ liệu theo giá trị của từng cột
	`showGlobalFilter`: Hiển thị thanh tìm kiếm toàn cọc cho phép người dùng tìm kiếm dữ liệu trong toàn bộ bảng
	`columnPining`: Cấu hình các cột cố định:
		`left`: Mảng chứa tên các cột cố định ở bên trái bảng. Trong ví dụ này, các cột 'mrrt-row-expand' và 'mrt-select': sẽ được cố định bên trái
		`right`Trong ví dụ, Mảng chứa tên các cột ở bên phải bảng. Cột 'mrt-row-action'  sẽ được cố định ở bên phải
	`paginationDisplayMode`
		`pages`: Hiển thị điều hướng phân trang theo số trang
	`positionToolbarAlertbanner`
		`bottom`: Đặt thanh thông báo ở phía dưới của bảng
	`muiSearchTextFieldProps`: 
	-**`size: 'small'`**: Thiết lập kích thước của trường tìm kiếm thành nhỏ.
	- **`variant: 'outlined'`**: Thiết lập kiểu dáng của trường tìm kiếm thành "outlined".

`muiPaginationProps`
- **`color: 'secondary'`**: Thiết lập màu sắc của điều hướng phân trang thành màu thứ cấp.
- **`rowsPerPageOptions: [10, 20, 30]`**: Cung cấp các tùy chọn số lượng hàng mỗi trang.
- **`shape: 'rounded'`**: Thiết lập hình dạng của các nút phân trang thành tròn.
- **`variant: 'outlined'`**: Thiết lập kiểu dáng của các nút phân trang thành "outlined".

### Style Element trong Table
1. `renderDetailPanel`: 
- Là một props trong Material React Table được sử dụng để tùy chỉnh nội dung hiển thị khi người dùng mở chi tiết của một hàng. 
- Nó cho phép bạn tạo ra một giao diện tùy chỉnh để hiển thị thông tin chi tiết về hàng đó
2. `renderRowActionMenuItem`
- **`renderRowActionMenuItems`** là một props trong Material React Table được sử dụng để định nghĩa các hành động có thể thực hiện trên từng hàng dữ liệu trong bảng.
- props này sẽ cho phép bạn tùy chỉnh danh sách các hành động mà người dùng có thể thực hiện trên mỗi hàng.

3. `renderTopToolbar`:
- **`renderTopToolbar`** là một props trong Material React Table cho phép bạn tùy chỉnh thanh công cụ trên cùng của bảng dữ liệu. 
- Thanh công cụ này thường chứa các nút hành động toàn cục như:
	- **Tìm kiếm:** Cho phép người dùng tìm kiếm dữ liệu trong toàn bộ bảng.
	- **Lọc:** Cho phép người dùng lọc dữ liệu dựa trên các tiêu chí khác nhau.
	- **Phân trang:** Cho phép người dùng điều hướng qua các trang dữ liệu.
	- **Các nút hành động khác:** Các nút tùy chỉnh khác mà bạn muốn thêm vào.
