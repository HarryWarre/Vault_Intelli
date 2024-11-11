Tags: #arcgis_exb #widget #map
Các trường đầu vào để tạo Map (WebMapDataSource)

### Jimumapview

```js
idMapRef = mvManager.getJimuMapViewById(id); // id widgets từ props
```

### Options Properties cho map
- Cấu hình MapView nếu chưa có JimuMapView
```js
const options: __esri.MapViewProperties = {
map: webmapDs.map,
container: mapContainer.current,
};
```

### Xử lý tham số URL và cập nhật phạm vi map (Extent)

```js
const queryObjectId = queryObject?.[id];
if (queryObjectId) {
  const extentStr = queryObjectId.substr("extent=".length);
  let extent;
  try {
    extent = new Extent(JSON.parse(extentStr));
  } catch (err) {
    setError({
      isError: true,
      message: "Bad extent URL parameter.",
    });
  }

  if (extent) {
    options.extent = extent;
  }
}
```

- queryObject: tham số các URL chứa dữ liệu và phạm vi bản đồ (**extent**)
	- Nếu tham số tồn tại (queryObjectId), nó sẽ được phân tích để tạo đối tượng Extent (phạm vi bản đồ)
	- Extent: Là hình chữ nhật đại diện cho vùng không gian mà bản đồ sẽ hiển thị
	- options.extent: Nếu phân tích **Extent** thành công, nó sẽ gán vào thuộc tính Extent trong MapViewProperties để bản đồ có phạm vi hiển thị chính xác

### Tạo JimuMapView với MapViewManager

```js
mvManager
  .createJimuMapView({
    mapWidgetId: id,
    view: new MapView(options),
    dataSourceId: webmapDs.id,
    isActive: true,
    mapViewManager: mvManager,
  })
```

- **mvManager.createJimuMapView**: Tạo một **JimuMapView** mới bằng cách truyền các tùy chọn cấu hình như:
    - `mapWidgetId`: ID của widget hiện tại.
    - `view`: Một đối tượng **MapView** mới được khởi tạo từ `options`.
    - `dataSourceId`: ID của **WebMapDataSource**.
    - `isActive`: Đặt **JimuMapView** ở trạng thái hoạt động.
    - `mapViewManager`: Sử dụng **MapViewManager** để quản lý bản đồ.

### Lắng nghe sự thay đổi phạm vi (extent)

```js
if (!extentWatch) {
  extentWatch = jimuMapView.view.watch(
    "extent",
    (extent: __esri.Extent) => {
      jimuHistory.changeQueryObject({
        [id]: `extent=${JSON.stringify(extent.toJSON())}`,
      });
    }
  );
}
```

- extentWatch: Sử dụng phương thức watch để lắng nghe sự thay đổi của thuộc tihs extent
- jimuHistory.changeQueryObject: Mỗi khi phạm vi thay đổi, URL sẽ cập nhật lại bằng cách chuyển đổi đối tượng Extent sang chuỗi JSON

### Reference 
- [Git - Create Map](https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/create-map/src/runtime/widget.tsx)