### 1. **Bối cảnh**

- **Biểu đồ cột**: Yêu cầu là tạo biểu đồ dạng cột (bar chart) để hiển thị dữ liệu số lượng sự cố.
- **Phân loại sự cố theo loại bể ngầm và bể nổi**: Biểu đồ phải thể hiện được số lượng sự cố, chia theo hai loại bể ngầm và bể nổi.
- **Thời gian**: Dữ liệu cần được phân bổ theo từng tháng, tức là trục thời gian (trục x) sẽ hiển thị các mốc thời gian theo tháng.

### 2. **Mục tiêu**

- **Khắc phục giới hạn của ArcGIS Experience Builder**: Mục tiêu là tạo một widget mới, vì widget chart hiện tại trong phiên bản ArcGIS Experience Builder v1.14 không đáp ứng đủ các yêu cầu về khả năng cấu hình linh hoạt.
- **Tính linh hoạt trong cấu hình**: Widget mới cần có khả năng cấu hình nhiều hơn, nhằm hiển thị dữ liệu chính xác và phù hợp với nhu cầu người dùng.

### 3. **Yêu cầu**

- **Group By và Category Field**:
    - `Category field`: Phải là trường kiểu **esriFieldTypeDate** – tức là widget này cần hỗ trợ dữ liệu theo ngày tháng, yêu cầu này là để widget tự động nhóm và hiển thị dữ liệu dựa trên mốc thời gian.
- **Chức năng Parse Dates**: Widget cần có chức năng **Parse dates** (phân tích và xử lý ngày tháng), cho phép phân tích các mốc thời gian để chia theo ngày, tháng, hoặc năm.
- **Minimum period**: Widget phải có khả năng hiển thị các khoảng thời gian nhỏ nhất (Minimum period) theo đơn vị **Day, Month, Year** – tức là người dùng có thể chọn khoảng thời gian nhỏ nhất mà họ muốn hiển thị, ví dụ như theo ngày, tháng, hoặc năm, tùy theo yêu cầu.

### Tóm tắt yêu cầu kỹ thuật chính

1. Widget biểu đồ cột hiển thị dữ liệu theo thời gian (theo tháng).
2. Khả năng phân loại dữ liệu theo bể ngầm và bể nổi.
3. Cấu hình linh hoạt, đặc biệt là nhóm dữ liệu và hiển thị theo ngày/tháng/năm.
4. Dữ liệu cần được nhóm và hiển thị dựa trên trường `esriFieldTypeDate`.