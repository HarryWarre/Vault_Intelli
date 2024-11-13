[Git link](https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/tab-table-view/src/runtime/function.ts#L312-L365)
Code
```js
export async function showAreaOnMap(
  jimuMapView: JimuMapView,
  point: any,
  blinkTimeNumber: number = 2
) {
  if (!jimuMapView) return;
  jimuMapView.view.graphics.removeAll();

  // Create a symbol for rendering the graphic
  let points: any = {
    type: "point",
    longitude: point.x,
    latitude: point.y,
    spatialReference: point.spatialReference,
  };

  // Create a symbol for rendering the graphic
  let markerSymbol = {
    type: "simple-marker",
    color: [230, 233, 22, 0.8],
    outline: {
      cap: "round",
      color: [230, 233, 22, 0.8],
      join: "round",
      miterLimit: 1,
      width: 2,
    },
  };

  // Add the geometry and symbol to a new graphic
  const pointGraphic = new Graphic({
    geometry: points,
    symbol: markerSymbol,
    // symbol: dhkhPointSymbol,
  });

  console.log(pointGraphic);

  // Add the graphics to the view's graphics layer
  const blinkTime = blinkTimeNumber;
  jimuMapView.view.graphics.add(pointGraphic);
  // console.log(jimuMapView.view.graphics);
  if (blinkTime > 1) {
    for (let i = 0; i < blinkTime; i++) {
      await new Promise((resolve) => setTimeout(resolve, defaultDsInterval));
      jimuMapView.view.graphics.remove(pointGraphic);
      console.log("Graphics before adding:", jimuMapView.view.graphics);
      await new Promise((resolve) => setTimeout(resolve, defaultDsInterval));
      jimuMapView.view.graphics.add(pointGraphic);
      console.log("Graphics after adding:", jimuMapView.view.graphics);
    }
  }
}
```


- Sử dụng bộ đếm `blinkTime`
- Cách hoạt động
	- Tạo một vòng lặp for với biến blinkTime
		- Tạo một Promise, với thời gian delay cố định `defaultDsInterval`
		- Lần lượt sau khoản delay, thực hiện xóa `remove` PointGraphic và sau delay Time lại add lại PointGraphic