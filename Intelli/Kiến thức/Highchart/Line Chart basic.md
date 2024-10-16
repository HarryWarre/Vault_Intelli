Tags: #highchart #linechart

Reference: [Line chart from HighChart](https://www.highcharts.com/demo/highcharts/line-chart)

# Introduce

![](https://www.highcharts.com/demo/images/samples/highcharts/demo/line-chart/thumbnail-brand-light.svg)


Một số props cần lưu ý:

```js
legend: {
        layout: 'vertical',
        align: 'right',
        verticalAlign: 'middle'
    },
```

Style legend bên phải nằm dọc

```js
plotOptions: {
        series: {
            label: {
                connectorAllowed: false
            },
            pointStart: 2010
        }
    },
```

- **`plotOptions`**:
    - Đây là đối tượng chính được sử dụng để tùy chỉnh các khía cạnh của biểu đồ, đặc biệt là cách các loại biểu đồ hoặc chuỗi dữ liệu cụ thể (series) được hiển thị. Trong trường hợp này, `plotOptions` đang thiết lập cho các **series** (chuỗi dữ liệu).
- **`series`**:
    - Thuộc tính này xác định các tùy chọn sẽ được áp dụng cho **tất cả các loại series** trên biểu đồ (ví dụ: line, column, pie, etc.). Trong phần này, bạn đang áp dụng cấu hình chung cho tất cả các series trong biểu đồ.
- **`label`**:
    - Đây là thuộc tính dùng để định nghĩa cách các nhãn (labels) của series được hiển thị hoặc kết nối.
    - **`connectorAllowed: false`**:
        - Thuộc tính này ngăn việc nối nhãn của các chuỗi dữ liệu (series) với các phần tử của chuỗi đó qua một đường dẫn (connector). Mặc định, khi không gian hiển thị biểu đồ quá chật hẹp hoặc có nhiều dữ liệu, Highcharts có thể tự động nối nhãn của một chuỗi với phần tử của nó bằng một đường kẻ. Bằng cách đặt `connectorAllowed: false`, bạn ngăn cản việc này, giúp biểu đồ gọn gàng hơn.
- **`pointStart`**:
    - Thuộc tính này chỉ định **năm bắt đầu** cho dữ liệu của series.
        
    - **`pointStart: 2010`**:
        - Điều này có nghĩa là dữ liệu của series sẽ bắt đầu từ năm 2010. Nếu không chỉ định, mặc định `pointStart` sẽ là `0`, tức là dữ liệu sẽ bắt đầu từ chỉ số `0`. Với `pointStart: 2010`, giá trị đầu tiên của trục x (ví dụ trong biểu đồ theo thời gian) sẽ là năm 2010, và các điểm dữ liệu tiếp theo sẽ tương ứng với các năm tiếp theo (hoặc đơn vị thời gian khác).
    