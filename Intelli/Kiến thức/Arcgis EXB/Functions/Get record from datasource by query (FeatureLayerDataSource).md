[Link git](https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/tab-table-view/src/runtime/widget.tsx#L178C3-L207C5)
Code mẫu 1:
```js
//Function query Dong Ho Khach Hang data from datasource (ref)
  const getDHKHData = async () => {
    if (isDataSourcesReady) {
      const featureLayer = dhkhRef.current as FeatureLayerDataSource;
      const queryParams: FeatureLayerQueryParams = {
        where: "",
        outFields: ["*"],
        returnGeometry: true,
      };

      const dataQuery = await featureLayer?.query(queryParams);
      dataQuery.records.forEach((element) => {
        setDHKHQuery((prevDHKHQuery) => [...prevDHKHQuery, element.getData()]);
      });
    }
  };
```

Code mẫu 2: 
```js
//Function query Thuy Dai data from datasource (ref)
  const getThuyDaiData = async () => {
    // console.log(jMapView);
    const featureLayer = thuyDaiRef.current as FeatureLayerDataSource;
    const dataQuery = await featureLayer?.query(queryAll);

    dataQuery.records.forEach((record) => {
      setThuyDaiQuery((prevThuyDaiQuery) => [
        ...prevThuyDaiQuery,
        record.getData(),
      ]);
    });
  };
```


