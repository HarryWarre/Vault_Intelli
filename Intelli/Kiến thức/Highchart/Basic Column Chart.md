Tags: #chart #colchart

Reference: [Highchart - Column Chart](https://www.highcharts.com/demo/highcharts/column-basic)

# Introduce
![](https://www.highcharts.com/demo/images/samples/highcharts/demo/column-basic/thumbnail-brand-light.svg)

Git link: [Mantis - Colchart](https://github.com/HarryWarre/Mantis-React-Intelli/blob/main/mantis-react/src/components/charts/config/col_chart.tsx)

```js
chart: {
        type: 'column'
    },
```
## Một số props chú ý
```js
xAxis: {
        categories: ['USA', 'China', 'Brazil', 'EU', 'India', 'Russia'],
        crosshair: true,
        accessibility: {
            description: 'Countries'
        }
    },
```

- `xAxis`: Cột x (horizontal)
	- categories: Dữ liệu trường ngang, tương ứng với mỗi dataset có trong data 

```js
yAxis: {
        min: 0,
        title: {
            text: '1000 metric tons (MT)'
        }
    },
```

- `yAxis`: trường dọc y (vertical)
	- min: 0 : Giá trị thấp nhất hiển thị là 0

```js
series: [
        {
            name: 'Corn',
            data: [406292, 260000, 107000, 68300, 27500, 14500]
        },
        {
            name: 'Wheat',
            data: [51086, 136000, 5500, 141000, 107180, 77000]
        }
    ]
});
```

- Mỗi dataset có 2 cột Corn và Wheat
