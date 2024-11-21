```js
chart: {
        type: 'pie'
    },
```

Loại chart: Pie

Giá trị phần trăm:
`tooltip: {valueSuffix: '%'},`

```js
plotOptions: {
        series: {
            allowPointSelect: true,
            cursor: 'pointer',
            dataLabels: [{
                enabled: true,
                distance: 20
            }, {
                enabled: true,
                distance: -40,
                format: '{point.percentage:.1f}%',
                style: {
                    fontSize: '1.2em',
                    textOutline: 'none',
                    opacity: 0.7
                },
                filter: {
                    operator: '>',
                    property: 'percentage',
                    value: 10
                }
            }]
        }
    },
```

Plot options:
- allowPointSelect: false `default`, true: Cho phép chọn các điểm Point biểu đồ
	- Được đẩy ra khỏi biểu đồ (dùng với thuộc tính sliced). Được đánh dấu bằng hiệu ứng viền hoặc **highlight**.
- distance: Khoảng cách của Point
- opacity: độ mờ, 
