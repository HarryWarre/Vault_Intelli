
### Khởi tạo và khai báo biến

- Support Types: Kiểu Datasource hỗ trợ cho widget: `FeatureLayer` và `SceneLayer`
- `translate`: Sử dụng `hooks.useTranslation` để hỗ trợ đa ngôn ngữ
- `seriesType`: Lấy loại biểu đồ hiện tại từ cấu hình `webChart`, mặc định là `barSeries`
- `outputDataSourceId` và `outputDataSourceLabel`: Xác định ID của nguồn dữ liệu đầu ra và nhãn cho dữ liệu đầu ra, dựa trên tên của widget.

### Hàm xử lý

- `handleUseDataSourceChange`: Xử lý khi người dùng chọn hoặc thay đổi dữ liệu nguồn (`dataSource`) cho biểu đồ.

- `handleOutputCreate`: Tạo một nguồn dữ liệu đầu ra mới khi cần.

- `handleFieldsChange`: Cập nhật các trường của `useDataSources` khi người dùng thay đổi trường dữ liệu đầu vào.

- `handleTemplateChange`: Cập nhật cấu hình widget khi thay đổi mẫu biểu đồ (template), đặt lại thuộc tính `tools` và `webChart`.

- `handleWebChartChange`: Cập nhật `webChart` trong cấu hình khi có thay đổi trong thiết lập của biểu đồ.

- `handleToolsChange`: Cập nhật công cụ (`tools`) của biểu đồ.

## [[SerialSetting]]

