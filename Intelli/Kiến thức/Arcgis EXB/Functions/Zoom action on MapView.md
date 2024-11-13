Code:

```js
export function zoomToMapByExtent(
  extent: __esri.Extent,
  _viewManager: MapViewManager,
  mapWidgetId: string
) {
  const mapView = getJimuMapView(mapWidgetId, _viewManager);

  mapView.then((jmv) => {
    jmv?.view?.goTo(extent);
  });
}
```

Sử dụng hàm
```js
// Zoom to a specific feature on the map based on the selected row data
  const handleZoomOnMap = async (rowData, featureLayerName) => {
    let featureLayer: FeatureLayerDataSource;
    switch (featureLayerName) {
      case "dhkh":
        featureLayer = dhkhRef.current as FeatureLayerDataSource;
        break;
      case "thuydai":
        featureLayer = thuyDaiRef.current as FeatureLayerDataSource;
        break;
      default:
        featureLayer = dhkhRef.current as FeatureLayerDataSource;
        break;
    }
    const dataQuery = await featureLayer.query(queryAll);

    const record = dataQuery.records.find(
      (r) => r.getData().OBJECTID === rowData.OBJECTID
    );

    // jMapView && zoomToPoint({ record });

    const point = new Point({
      x: record.getGeometry()["x"],
      y: record.getGeometry()["y"],
      z: record.getGeometry()["z"], // Optional
      spatialReference: record.getGeometry()["spatialReference"],
    });

    const buffer = 1;

    if (jMapView && _viewManager) {
      const extent = new Extent({
        xmin: point.x - buffer,
        ymin: point.y - buffer,
        xmax: point.x + buffer,
        ymax: point.y + buffer,
        spatialReference: point.spatialReference,
      });

      await zoomToMapByExtent(extent, _viewManager, mapWidgetId);
      // zoomToPoint({ record });
      await showAreaOnMap(jMapView, point, 5);
    }
  };
```


Xem thêm:
- [[Hiển thị tài sản theo mode Flash (nhấp nháy)]]