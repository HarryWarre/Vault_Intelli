Tags: #chart #areachart
Reference: [Highchart - Basic Area](https://www.highcharts.com/demo/highcharts/area-basic)
# Introduce

Git link: [Mantis - Area Chart](https://github.com/HarryWarre/Mantis-React-Intelli/blob/main/mantis-react/src/components/charts/config/month_visitor_area_chart.tsx)

![](https://www.highcharts.com/demo/images/samples/highcharts/demo/area-chart/thumbnail-brand-light.svg)

Một số props chú ý:
```js
plotOptions: {
        area: {
            pointStart: 1940,
            marker: {
                enabled: false,
                symbol: 'circle',
                radius: 2,
                states: {
                    hover: {
                        enabled: true
                    }
                }
            }
        }
    },
```

Thực hiện tạo marker, mặc định không có, 
 - `pointStart` thời điểm bắt đầu tại đây là 1940
 - marker symbol: hình dạng marker
 - hover: Thực hiện khi hover
	 - enable: true => Thực hiện tạo marker khi hover