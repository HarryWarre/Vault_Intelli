### **FeatureLayer URL**
Ref: [[Feature Layer]]
- **Cách sử dụng**: Query trực tiếp từ **URL** của `FeatureLayer` thông qua lớp `FeatureLayer` của ArcGIS API.
- **Trực tiếp và linh hoạt**: Hỗ trợ đầy đủ các truy vấn và thao tác của API như `createQuery()`, `queryFeatures()`, và có thể sử dụng các điều kiện phức tạp.
- **Khả năng truy vấn độc lập**: Phù hợp cho các thao tác nhanh, không phụ thuộc vào cấu trúc dữ liệu của ứng dụng ArcGIS Experience Builder.
Input: 
- URL của Server
code:
```js
// Query DMA by url
export const queryDMA = async () => {
try {
	const dmaURL = `${BASE_URL_Server}/${layerIds.dma}`; // url
	const DMALayer: FeatureLayer = createFeatureLayer(dmaURL);
	const queryParams = DMALayer.createQuery();
	queryParams.where = `1 = 1`;
	const results = await DMALayer.queryFeatures(queryParams);
	const mappingResults = results.features.map((f) => f.attributes);
	console.log(mappingResults);
	return results;
} catch (error) {}
};
const createFeatureLayer = (url) => {
	return new FeatureLayer({
		url: url,
	});
};
```

### 2. **FeatureLayerDataSource**

- **Cách sử dụng**: Thông qua ArcGIS Experience Builder, `FeatureLayerDataSource` lấy dữ liệu từ các nguồn được cấu hình sẵn trong ứng dụng và dễ dàng tích hợp với các widget khác.
- **Tích hợp cao trong Experience Builder**: `FeatureLayerDataSource` là một lớp đặc biệt cho phép làm việc dễ dàng với các nguồn dữ liệu đã được cấu hình và chia sẻ trong ArcGIS Experience Builder.
- **Truy vấn bị giới hạn**: Một số tính năng của ArcGIS API có thể bị giới hạn hoặc yêu cầu thêm cấu hình khi sử dụng `FeatureLayerDataSource`.
- **Tính nhất quán và quản lý trong Experience Builder**: **Phù hợp khi cần đồng bộ dữ liệu** với các thành phần khác trong ứng dụng.

Các input cần: 
- Datasource: 
```js
const dsArr: DataSource[] = [];
props.useDataSources?.forEach((useDataSource, index) => {
const ds = DataSourceManager.getInstance().getDataSource(
useDataSource?.dataSourceId
);
dsArr.push(ds);
})

if (dsArr.every((e) => e)) {
setIsDataSourceReady(true);
DMARef.current = dsArr[2];
DHKHRef.current = dsArr[0];
ThuyDaiRef.current = dsArr[1];
```

vd:
```js
const getDMAData = async (ds: DataSource) => {
const _ds = ds as FeatureLayerDataSource; // Chuyển đổi sang FeatureLayerDataSource
if (_ds) {
const countTotal = await _ds.query({
	// Query params here --------------------> Can Split to const queryParams = {structure of params} if needs
	// outFields: ["*"],
	outFields: dmaQueryAtribute,
	where: "OBJECTID is not null",
	returnGeometry: true,
	page: page,
	pageSize: pageSize,
});

await queryDMA();
	setDataDMA(countTotal);
}
};
```
### Tóm tắt

- **FeatureLayer URL**: Tối ưu cho truy vấn độc lập, linh hoạt, trực tiếp qua API.
- **FeatureLayerDataSource**: Tối ưu cho ứng dụng trong Experience Builder, dễ quản lý và tích hợp trong các widget của ArcGIS.

Một số link git tham khảo:

FeatureLayer URL:
https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/9222a1b3eec1f006fd4d7d505d99c8f0363ec742/your-extensions/widgets/view-data-map/src/runtime/function.ts#L73-L96
FeatureLayerDatasource:
https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/9222a1b3eec1f006fd4d7d505d99c8f0363ec742/your-extensions/widgets/view-data-map/src/runtime/widget.tsx#L225-L240



# Ưu và nhược điểm 2 loại 
### 1. **FeatureLayer sử dụng URL**

- **Ưu điểm**:
    - **Dễ dàng truy cập dữ liệu trực tuyến**: Có thể liên kết trực tiếp đến dịch vụ dữ liệu trên ArcGIS Server hoặc ArcGIS Online.
    - **Tự động cập nhật dữ liệu**: Khi nguồn dữ liệu thay đổi, các thay đổi sẽ tự động phản ánh trên bản đồ mà không cần thao tác thêm.
    - **Tương thích tốt với các dịch vụ web GIS**: Có thể dễ dàng sử dụng các URL từ các dịch vụ web phổ biến và được hỗ trợ bởi nhiều nền tảng ArcGIS.
- **Nhược điểm**:
    - **Phụ thuộc vào kết nối mạng**: Cần có kết nối ổn định để truy cập dữ liệu, nếu không, có thể gặp vấn đề về hiệu suất hoặc không tải được dữ liệu.
    - **Ít tùy chỉnh dữ liệu trực tiếp trong ExB**: Các thao tác tùy chỉnh dữ liệu phải thực hiện qua dịch vụ chứ không thể chỉnh sửa dễ dàng trong Experience Builder.

### 2. **FeatureLayerDatasource**

- **Ưu điểm**:
    - **Tích hợp tốt trong ArcGIS Experience Builder**: FeatureLayerDatasource cung cấp khả năng tích hợp và quản lý dữ liệu ngay trong ExB, giúp dễ dàng tạo các tương tác động với bản đồ.
    - **Quản lý dữ liệu tốt hơn**: Có thể cấu hình chi tiết dữ liệu ngay trong ExB, dễ dàng cho việc thiết kế và kiểm soát nội dung hiển thị.
- **Nhược điểm**:
    - **Phụ thuộc vào cấu hình trong ExB**: Cần thực hiện các bước cấu hình chi tiết, có thể phức tạp và mất thời gian
    - **Khả năng cập nhật dữ liệu**: Nếu dữ liệu nguồn thay đổi, có thể cần phải làm mới hoặc tái cấu hình datasource để phản ánh dữ liệu mới.