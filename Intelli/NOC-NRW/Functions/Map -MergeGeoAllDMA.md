Tên function: getMergeGeometryAllDMA
Input: paramProfileId (String)

Phương thức querry: Feature Layer

Querry Params
```js
const queryParams = fLDMA_NRW.createQuery();
if(!profileId){
queryParams.where = `1 = 1`;
}else{
queryParams.where = `${profileIdKey} = '${
	paramProfileId ? paramProfileId : profileId
}'`;
}

queryParams.outFields = [
OBJECTIDKey,
ID_DMA_Key,
id_DMA_Key,
TyLeThatThoat_NRW_Key,
keySetLayerDMANRW
];

queryParams.returnGeometry = true;
```

Get data từ result sau khi query
```js
const dataDMA_NRW = results.features.map((f) => f.attributes);
const dmaIds = results.features.map((f) => f.attributes?.[keySetLayerDMANRW]);//OBJECTIDKey changed to ID_DMA_Key
const geometryList = results.features.map((f) => f.geometry);
const mergeGeometry =
geometryList.length > 0 ? geometryEngine.union(geometryList) : null;

return { dmaIds, mergeGeometry, dataDMA_NRW };
```

Hậu xử lý sau khi Merge Geometry

```js
getMergeGeometryAllDMA().then(
        profileId,
        ({ dmaIds, mergeGeometry, dataDMA_NRW }: any) => {
          if (dmaIds && dmaIds?.length > 0) {

            // const expression = `${OBJECTIDKey} in (${dmaIds.join(",")})`;
            const expression = `${keySetLayerDMANRW}  in (${dmaIds.join(",")})`;
            changeDefinitionExpressionAndGoto(
              "show All DMA",
              mapWidgetId,
              expression,
              0,
              mergeGeometry
            );

            // handle data for chart
            const dataChart: any[] =
              handleConvertDataForChart(dataDMA_NRW) || [];
            setDataChartPie([...dataChart]);

            // set state redux
            props.dispatch(
              appActions.widgetStatePropChange(
                storeParentKey.company,
                storeKey.dataCompany,
                {
                  period: periodSelected,
                  year: yearSelected.year(),
                }
              )
            );
          }
        }
      );
```

- Chỉ hiển thị các vùng DMA có trong query

- Handle Data to chart:
	- Xử lý: Đếm và phân loại tỉ lệ thất thoát nước
```js
const counts = DMAList.reduce((acc, item) => {
	const { TyLeThatThoat_NRW } = item;
		for (let i = 0; i < categories.length; i++) {
		if (
		TyLeThatThoat_NRW > categories[i].min &&
		TyLeThatThoat_NRW <= categories[i].max
	) {
		acc[i]++;
		break;
	}
	}
		return acc;
	}, initialCounts
);
```

- Sử dụng reduce để phân loại và đếm số phân tử trong một list dựa trên giá trị thuộc tính `TyLeThatThoatNuoc_NWR`, so sánh các khoảng giá trị được định nghĩa trong categories. 
- Kết quả trả về một mảng count chứa số lượng từng mục

Input:
- DMA List
- categories: Mảng danh mục, mỗi loại có chứa min max, xác định khoảng giá trị để phân loại
- initialCount

Khởi tạo ban đầu, mỗi loại đều là 0:
```js
const initialCounts = categories.map(() => 0);
```

Hoạt động reduce: 
- acc: accumulator kết quả trước đó
- item: Phần tử hiện tại

Cách xử lý: 
Lấy giá trị item trong list, duyệt qua từng mục categories bằng for
- So sánh min max ? tăng dần + break