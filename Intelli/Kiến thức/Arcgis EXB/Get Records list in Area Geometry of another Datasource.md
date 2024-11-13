Hàm dùng để get danh sách các records có trong một vùng địa lý của một vùng tài sản datasource khác

Ví dụ: lấy danh sách các đồng hồ khách hàng có trong một DMA

[Code:](https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/view-data-map/src/runtime/function.ts#L49-L71)
```js
export const getDHKHIDsInGeometry = async (
  record: DataRecord,
  datasource: any // Thay 'any' bằng kiểu của datasource nếu biết
): Promise<string[]> => {
  const queryParams: FeatureLayerQueryParams = {
    where: "",
    outFields: ["*"],
    returnGeometry: true,
    geometry: record.getGeometry(),
  };

  try {
    const data = await datasource?.query(queryParams);
    const customerIDs = data.records.map(
      (r: DataRecord) => r.getData()["OBJECTID"]
    );

    return customerIDs;
  } catch (error) {
    console.log("Error fetching customer IDs:", error);
    return [];
  }
};
```

