
Code:
```js
const Widget = (props: AllWidgetProps<any>) => {
  const [latitude, setLatitude] = useState<String>("");
  const [longtitude, setLongtitude] = useState<String>("");

  const activeViewChangeHandle = (jmv: JimuMapView) => {
    if (jmv) {
      //When the pointer moves, take the pointer location and create a Point
      //Geometry out of it ('view.toMap(...)') then update the state

      jmv.view.on("pointer-move", (evt) => {
        const point: Point = jmv.view.toMap({
          x: evt.x,
          y: evt.y,
        });

        setLatitude(point.latitude.toFixed(3));
        setLongtitude(point.longitude.toFixed(3));
      });
    }
  };
```

Giải thích:
- Hàm này sử dụng jimumapview, sử dụng `pointer-move` để thực hiện event track con trỏ chuột, từ đó get được Point
- set state cho 2 phần