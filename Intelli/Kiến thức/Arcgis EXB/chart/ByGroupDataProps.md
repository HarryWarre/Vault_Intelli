- Là một giao diện tùy chỉnh cho cài đặt dữ liệu thống kê. 

# **Component `ByGroupData`**:
- `useState` để theo dõi trạng thái tải của dữ liệu ngày tháng (`loadingDate`).

- `useMemo` được sử dụng để tính toán và lưu trữ giá trị của các thuộc tính phụ thuộc vào dữ liệu nguồn, chẳng hạn như `objectidField`, `categoryFieldType`, và `splitByFieldValues`.

handleCategoryFieldChange
- Cập nhật trường danh mục khi có sự thay đổi. Nếu trường danh mục là kiểu ngày (`Date`), nó sẽ kích hoạt `time binning`, tức là phân loại theo khoảng thời gian.
- `orderByFields` được thiết lập mặc định là `ASC` để sắp xếp danh mục theo thứ tự tăng dần.
- Nếu có thay đổi thành công, nó sẽ cập nhật `chartDataSource` và gọi hàm `onChange` để thông báo cho các thành phần liên quan.

`handleStatisticTypeChange`:
    - Cập nhật loại thống kê (vd: đếm, tổng, trung bình,…) dựa trên thay đổi của người dùng và cập nhật `chartDataSource`.

**Chức năng `handleNumericFieldsChange`**:
        - Cập nhật các trường dữ liệu số khi người dùng chọn hoặc bỏ chọn trường và cập nhật `chartDataSource`.
 **Chức năng `handleSplitByFieldChange`**:
        - Xử lý thay đổi trường "Split By" khi người dùng chọn hoặc bỏ chọn một trường chia nhỏ và cập nhật `chartDataSource`.
**Time Interval và Time Aggregation**:
        - `handleTimeIntervalChange`, `handleTimeAggregationTypeChange`, `handleNullPolicyChange`, và `handleTrimIncompleteTimeIntervalChange` là các hàm để xử lý thay đổi trong cài đặt khoảng thời gian và cách biểu đồ xử lý các giá trị null hoặc thời gian không đầy đủ.
**Hiển thị Giao diện**:
        - `SettingRow` và các component con được sử dụng để tạo các hàng giao diện cho từng phần cài đặt, bao gồm:
            - `FieldSelector` để chọn trường danh mục hoặc trường số.
            - `StatisticsSelector` để chọn loại thống kê.
            - `SplitByField` cho trường chia nhỏ dữ liệu nếu được hỗ trợ.
            - `TimeBinning` cho cài đặt khoảng thời gian nếu biểu đồ là dạng chuỗi thời gian.
            - `SorteSetting` để chọn trường sắp xếp khi không sử dụng `time binning`.