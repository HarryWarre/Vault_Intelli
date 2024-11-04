
Constant:
https://cloud.intelli.com.vn/server/rest/services/Devonly/QUANLYTAISAN_GISCHOLON_V1/FeatureServer/1


với 
url server: https://cloud.intelli.com.vn/server/rest/services/Devonly/QUANLYTAISAN_GISCHOLON_V1/FeatureServer/

DHKH: 1 (id của layer)

Cấu trúc của việc query bằng URL sử dụng 
```js
const getCareTaker = async () => {
    try {
      const layerNRWUrl = LayerSources.NRWLayerUrl;

      const careTakerLayer: FeatureLayer = createFeatureLayer(
        layerNRWUrl.careTaker
      );

      const queryParams = careTakerLayer.createQuery();

      queryParams.where = `1 = 1`;

      const results = await careTakerLayer.queryFeatures(queryParams);

      const mappingResults = results.features.map((f) => f.attributes);

      setCareTakers([...mappingResults]);

      return results;
    } catch (error) {}
  };
```

- `layerNRWUrl`: layer url như bên trên, là một constant

- `careTakerLayer` là một đối tượng `FeatureLayer`, được tạo từ hàm `createFeatureLayer` với URL của lớp `careTaker`.

- `createFeatureLayer` có thể là một hàm tiện ích (utility function) được định nghĩa ở nơi khác trong mã để tạo một đối tượng `FeatureLayer` dựa trên URL được cung cấp.

- `queryParams` là một đối tượng tham số truy vấn (`Query`) được tạo bằng phương thức `createQuery()` của `careTakerLayer`. Đối tượng này chứa các thông số để định nghĩa cách thức truy vấn.

- `queryParams.where = '1 = 1'` là câu điều kiện truy vấn

- `results` là kết quả của truy vấn, trả về danh sách các đối tượng (`features`) từ lớp bản đồ, dựa trên tham số `queryParams`.

- `appingResults` là một mảng chứa thuộc tính của mỗi đối tượng (feature) trong kết quả truy vấn. `map()` được sử dụng để trích xuất thuộc tính (`attributes`) của từng đối tượng.


convert datasource thành FeatureLayer thì dùng :
```js
const dsDMZ = await (
        _getFeatureLayerDataSource(
          idDataSource?.DMZFeatureLayerId
        ) as FeatureLayerDataSource
      ).createJSAPILayerByDataSource();
```

```js
export function _getFeatureLayerDataSource(dataSourceId: string) {
  return DataSourceManager.getInstance().getDataSource(dataSourceId) as
    | FeatureLayerDataSource
    | undefined;
}
```

Lấy FeatureLayer từ một FeatureLayerDataSource trong ArcGIS EXB. `FeatureLayerDataSource` là kiểu dữ liệu được ArcGIS exb sử dụng để quả lý dữ liệu từ một lớp (layer), còn `FeatureLayer` là đối tượng của ArcGIS API for JS được dùng để truy vấn và hiển thị dữ liệu

- Hàm `_getFeatureLayerDataSource` dùng để lấy `FeatureLayerDataSource` từ một `DataSourceId`.

-  **getDataSource(dataSourceId)**: Phương thức `getDataSource` tìm `DataSource` theo ID được cung cấp (`dataSourceId`).

