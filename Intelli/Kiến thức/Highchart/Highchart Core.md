Tags: #chart #highchart
Version: Highchart version 11.4.8
# Understanding Highchart
Reference: [Understanding Highchart](https://www.highcharts.com/docs/chart-concepts/understanding-highcharts)

## Cấu trúc của highchart
- title: Tiêu đề
	- subtitle: tiêu đề con, mặc định nằm dưới tiêu đề
 ```js
title: {
    text: 'My custom title'
},
subtitle: {
    text: 'My custom subtitle'
}
```
- serries: đường, cột, biểu đồ hiển thị dữ liệu
- Tooltips: Bảng mô tả khi hover vào biểu đồ
- Axes: Cột X, Y
- Legend: Các tên của loại dữ liệu

![[Pasted image 20241015113932.png]]

### Axis labels, tickmarks and gridlines
The axis labels, tickmarks and gridlines are closely linked and all scale together. Their positioning is calculated to best fit the data present in a chart.

![[Pasted image 20241015114222.png]]

### Ticks

Tick là những dấu gạch nhỏ được đặt dọc theo trục của biểu đồ để thể hiện đơn vị đo lường. Khoảng cách giữa các tick được quyết định chủ yếu bởi các tùy chọn `tickInterval` và `tickPixelInterval`. Các nhãn và đường lưới được sắp xếp ở cùng vị trí với các tick.

#### Tùy chọn `tickInterval`

- **Mục đích:** Quyết định khoảng cách giữa các tick theo đơn vị đo lường của trục.
- **Giá trị mặc định:** `null`.
- **Hành vi:**
    - Khi `tickInterval` là `null`:
        - Trên trục tuyến tính và thời gian: Khoảng cách giữa các tick được tính toán gần đúng theo `tickPixelInterval`.
        - Trên trục phân loại: Khoảng cách giữa các tick mặc định là 1 đơn vị (một danh mục).
    - Khi `tickInterval` được đặt thành một giá trị khác:
        - Trên trục tuyến tính và thời gian: Khoảng cách giữa các tick sẽ theo giá trị đã đặt.
        - Trên trục thời gian: Giá trị phải được tính bằng mili giây.
        - Trên trục logarit: Giá trị là số mũ. Ví dụ, `tickInterval` bằng 1 có nghĩa là một tick trên mỗi bậc 0.1, 1, 10, 100, v.v.

### Tùy chọn `tickPixelInterval`

- **Mục đích:** Thiết lập khoảng cách pixel xấp xỉ giữa các tick.
- **Giá trị mặc định:** 72 cho trục y và 100 cho trục x.
- **Hành vi:**
    - Chỉ áp dụng cho trục tuyến tính và thời gian.
    - Giúp đảm bảo khoảng cách giữa các tick hợp lý, không phụ thuộc vào kích thước của biểu đồ và độ dài của trục.

**Ví dụ:**
```js
Highcharts.chart('container', {
    xAxis: {
        tickInterval: 1000 * 60 * 60 * 24, // Một ngày
        tickPixelInterval: 72
    },
    yAxis: {
        tickInterval: 10,
        tickPixelInterval: 100
    },
    series: [{
        data: [29.9, 71.5, 106.4, 129.2, 144.0, 176.0, 135.6, 148.5, 216.4, 194.1, 95.6, 54.4]
    }]
});
```

### Minor Ticks
-  **Mục đích:** Đặt các dấu tick nhỏ giữa các dấu tick chính.
- **Tùy chọn:** `minorTickInterval`
- **Hành vi:** Khi `minorTickInterval` được đặt, các tick nhỏ sẽ được bố trí giữa các tick chính. Điều này bao gồm các dấu tick nhỏ và đường lưới nhỏ, nhưng không bao gồm nhãn.

### Đường lưới (Grid Lines) trong Highcharts

**Đường lưới** là tập hợp các đường ngang và/hoặc dọc chia biểu đồ thành lưới, giúp dễ dàng đọc các giá trị trên biểu đồ.

#### Kích hoạt và vô hiệu hóa đường lưới

Để kích hoạt hoặc vô hiệu hóa đường lưới cho trục x hoặc trục y, bạn đặt thuộc tính `gridLineWidth` của trục tương ứng:

```js
xAxis: {
    gridLineWidth: 1 // Kích hoạt đường lưới ngang
},
yAxis: {
    gridLineWidth: 1 // Kích hoạt đường lưới dọc
}
```
#### Đường lưới nhỏ (Minor Grid Lines)

- **Kích hoạt:** Để kích hoạt đường lưới nhỏ, bạn đặt thuộc tính `minorTickInterval`. Điều này sẽ đặt các đường lưới nhỏ giữa các đường lưới chính.
### Axis types
An axis can be:
either, linear, logarithmic, datetime or categories. 
The axis type is set like this:
```js
// The types are 'linear', 'logarithmic' and 'datetime'
yAxis: {
    type: 'linear',
}
// Categories are set by using an array
xAxis: {
    categories: ['Apples', 'Bananas', 'Oranges']
}
```


## Series

### What is a series?

A series is a set of data, for example a line graph or one set of columns. All data plotted on a chart comes from the series object. The series object has the structure:
```
series: [{
    name: '',
    data: []
}]
```
### [List Array](https://jsfiddle.net/gh/get/library/pure/highcharts/highcharts/tree/master/samples/highcharts/series/data-array-of-arrays/)
List of arrays with two or more values. In this case, the first value is the x value and the second is the y value
If the first value is a string, it is applied as the name of the point, and the x value is incremented following the above rules.

```
data: [[5, 2], [6, 3], [8, 2]]
```

### [A list of objects with named values](https://jsfiddle.net/gh/get/library/pure/highcharts/highcharts/tree/master/samples/highcharts/series/data-array-of-objects/) 
In this case the objects are point configuration objects as seen under options.point.
The full list of available properties can be seen from the API, for [example for line series](https://api.highcharts.com/highcharts/series.line.data).

```
data: [{
    name: 'Point 1',
    color: '#00FF00',
    y: 0
}, {
    name: 'Point 2',
    color: '#FF00FF',
    y: 5
}]
```


