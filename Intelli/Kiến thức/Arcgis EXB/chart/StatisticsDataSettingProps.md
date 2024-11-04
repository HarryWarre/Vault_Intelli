Là một component quản lý cấu hình dữ liệu thống kê cho biểu đồ trong Arcgis EXB

# Props chính
- `type`: Xác định loại biểu đồ (e.g., `barSeries`, `lineSeries`), từ đó ảnh hưởng đến cách hiển thị dữ liệu và các lựa chọn cấu hình.
- `series`: Mảng bất biến chứa các đối tượng cấu hình cho chuỗi dữ liệu biểu đồ.
- `chartDataSource`: Đối tượng bất biến chứa các thông tin về nguồn dữ liệu của biểu đồ, bao gồm các thiết lập như `query` (truy vấn).
- `useDataSources`: Mảng bất biến chứa danh sách các nguồn dữ liệu được dùng.
- `onChange`: Callback được gọi khi có thay đổi trong cấu hình để cập nhật `series` và các thông tin liên quan.


## Xác định loại category

**`CategoryType.ByGroup` và `CategoryType.ByField`** là hai loại Category chính để hiển thị dữ liệu:

- **`ByGroup`**: Dữ liệu được nhóm lại dựa trên một trường nhất định.
- **`ByField`**: Sử dụng các trường cụ thể làm nhóm dữ liệu.

### **Xử lý Sự Kiện Thay Đổi**:

- **`handleCategoryTypeChange`**: Cập nhật `categoryType` khi người dùng chọn loại category mới, tạo lại `series` và `query` mặc định dựa trên loại Category đã chọn.

- **`handlePageSizeChange` và `handleAcceptPageSize`**: Được dùng để thiết lập và xác nhận số lượng mục tối đa (`maxCategories`) hiển thị trên biểu đồ.


[[ByGroupDataProps]]
