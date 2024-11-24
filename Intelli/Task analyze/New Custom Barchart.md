# Phase 1 : BA chức năng chi tiết 

#### **Phân tích nhu cầu giao diện**

1. **Giao diện chính**
    - **Mục đích**: Hiển thị biểu đồ cột trực quan, phân tích dữ liệu theo thời gian (ngày, tháng, năm).
    - **Đặc điểm cần có:**
        - Các cột biểu diễn số lượng sự cố.
        - Trục hoành (X-axis) biểu diễn thời gian (mặc định theo tháng, có thể điều chỉnh).
        - Trục tung (Y-axis) biểu diễn số lượng sự cố.
        - Phân loại sự cố theo loại bể ngầm và bể nổi (có thể dùng màu sắc khác nhau để phân biệt).
2. **Tính năng cấu hình (Configuration Panel)**
    - **Giao diện cấu hình linh hoạt**:
        - Chọn trường dữ liệu từ bảng để làm **Category field** (Group By).
        - Hỗ trợ trường dữ liệu kiểu **esriFieldTypeDate** để nhóm dữ liệu theo ngày, tháng, hoặc năm.
        - Chức năng "Parse dates" để xử lý định dạng ngày/tháng/năm phù hợp.
        - Tùy chọn "Minimum period" để đặt chu kỳ tối thiểu (ngày, tháng, năm).
        - Statistic: Phân loại thống kê theo từng phần
        - Split by field: Chọn loại dữ liệu để phân theo dữ liệu chính
        - Sort by: Sắp xếp dữ liệu hiển thị theo gì ?
	        - **Ascending (Tăng dần)** và **Descending (Giảm dần)** trục x
	        - Value và Category: sắp xếp theo nhóm / giá trị
1. **Yêu cầu về giao diện người dùng (UI)**
    - **Trực quan hóa dữ liệu:**
        - Màu sắc nổi bật để phân biệt loại bể (ngầm, nổi).
        - Nhãn (labels) rõ ràng cho từng thanh (cột) của biểu đồ. (vị trí, size, màu sắc, không đè chữ trong trường hợp label quá dài `Vị trí trên dưới cho 2 label dài trong trường hợp có thể đè chữ`)
    - **Tương tác người dùng:**
        - Chọn hoặc lọc dữ liệu trực tiếp trên giao diện.
        - Hiển thị chi tiết khi người dùng hover chuột vào cột (tooltip).
2. **Tùy chỉnh hiển thị**
    - Hỗ trợ thay đổi các yếu tố của biểu đồ:
        - Thay đổi màu sắc và kiểu hiển thị.
        - Cấu hình khoảng cách giữa các cột.
        - Thay đổi nhãn hoặc kiểu chữ. (màu sắc, size).
# Phase 2 : Tạo giao diện Bar chart
- [x] Chuyển sang sử dụng range selector, code mẫu trong source NOC-NRW
- [x] Tắt tính năng zoom
- [x] Tắt tính năng export
- [ ] Tạo setting và đưa các props vào trong setting, chuyển sang dạng object
- [ ] Update setting thêm các props cần thiết 
- [ ] Tạo chức năng thống kê khác ngoài Count
# Phase 3 : Config theo giao diện mẫu
# Phase 4 : Custom setting

Danh sách setting lần 1
- [x] Group By - Datasource key value (file common)
- [x] Split By - Datasource key value (file common)
- [x] Parse Date - List (Date, Month, Year)
- [x] is SplitBy - toggle (boolean)
- [x] chartType - List (Col, bar, line)
- [x] chartHeight: input (number)

- [x] Chart Title - Input - Text
- [x] Chart Subtitle - Input - Text

isParseDate - Type of atribute in category
- [ ] isParseDate
- [ ] Type category ? 

- Bị lỗi:
	- Hiện tại sẽ có lỗi nhỏ nếu như chọn đổi Split by, chart sẽ reset không toàn bộ 
		- Result: Sử dụng query mỗi khi isSplitBy đổi
	- Chart hiện tại chỉ hoạt động đối với loại date category là dạng ngày ()

- Plan tạo list select fields trong layer datasource
	- [x] 1. Tạo một DatasourceComponent để lấy được nguồn dữ liệu
	- [x] 2. Query để lấy danh sách các fields hiện có
	- [x] 3.  Lấy type của fields hiện tại.
- mẫu lấy alias: tab-table view

- [x] Kết nối select và props với nhau
- [x] Tạo IsparseDate
- [x] Tạo chart khi không phải là date


Date
139, 11, 47, 107
Month
139, 47, 107, 11

# **Phase 5: Fix bug**

- [x] Tối ưu `useEffect` cho các phần source runtime hiện tại.
- [x] Sửa và xóa import ngoài widget.

# **Phase 6: Sửa tính năng liên quan đến datasource**

- [x] Sửa logic query để lấy toàn bộ record (hiện tại chỉ lấy được 2000 record):
    - Query setting.
    - Query runtime (Data of chart, series values).
- [x] Lấy dữ liệu từ `DataSource`.

# **Phase 7: Thêm tính năng giao diện**

- [x] Hiển thị mô tả của giá trị nếu trường có **Domain**. (default 3)
- [x] Cho phép bật/tắt hiển thị số lượng trên chart. (Đã bật)
- [ ] Cho phép thay đổi màu sắc chart, cỡ chữ, kiểu chữ (**Appearance**).
- [ ] Đổi màu sắc từng series.
- [ ] Hiển thị màu sắc cho title, sub title

Chọn màu sắc cho từng serries
- [ ] Query danh sách serries tồn tại khi đã chọn Split By và Category
- [ ] Tạo một List gồm tên serries - Color Picker
- [ ] Gửi vào props setting

- [ ] Tạo object trong runtime
- [ ] Thêm màu sắc nếu có tồn tại name serri  = name trong object

# **Phase 8: Nghiên cứu về action trigger, filter on chart**

- Nghiên cứu về **action trigger** và áp dụng lên chart.
- Nghiên cứu về **filter** và áp dụng lên chart.

*Lấy dữ liệu datasource*
Hiển thị màu sắc
Đổi màu serries
Hiển thị trường domain

querycount

"30042200323"
"30042200323"

Không có date trong splitby

Filter document
