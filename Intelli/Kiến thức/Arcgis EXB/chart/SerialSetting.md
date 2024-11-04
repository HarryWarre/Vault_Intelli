
Cấu hình ho biểu đồ tuần tự (serial Charts) như bar, lines

Cấu trúc này bao gồm các thành phần cài đặt cho dữ liệu, chuối dữ liệu (serries), trục axes, cài đặt chung và giao diện. Dưới đây là giải thích chi tiết


## SerialSettingProps
- **`type`**: Xác định loại biểu đồ (ví dụ: biểu đồ cột hoặc biểu đồ đường).
- **`section`**: Phần hiện tại của giao diện cài đặt mà người dùng đang tương tác (Data, Series, Axes, General, Appearance).
- **`webChart`**: Cấu hình biểu đồ hiện tại được truyền vào dưới dạng một đối tượng `IWebChart`.
- **`useDataSources`**: Nguồn dữ liệu sử dụng trong biểu đồ.
- **`onSectionChange`**: Hàm gọi khi người dùng thay đổi giữa các phần (section) khác nhau trong giao diện cài đặt.
- **`onWebChartChange`**: Hàm gọi khi có thay đổi trong cấu hình `webChart`.


### Các thành phần chính 

a. **Data Setting (Cài Đặt Dữ Liệu)**
- [[StatisticsDataSettingProps]]
b. **Series Setting (Cài Đặt Chuỗi Dữ Liệu)**
c. **Axes Setting (Cài Đặt Trục)**
d. **General Setting (Cài Đặt Chung)**
e. **Appearance Setting (Cài Đặt Giao Diện)**


3. **Cấu Trúc Của SettingSection và SettingCollapse**

- **`SettingSection`**: Đóng vai trò như phần tử bố cục, mỗi `SettingSection` là một nhóm cài đặt khác nhau.
- **`SettingCollapse`**: Cho phép ẩn hoặc hiện các nhóm cài đặt trong `SettingSection`