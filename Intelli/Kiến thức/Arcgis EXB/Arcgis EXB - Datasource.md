Tags: #arcgis_exb #datasource #setting
# Interface

## Types
- Main datasource: 
	- Datasource user added in data panel
- DataView: the data view user created in datapanel
- Local Datasource: when multiple widgets connect to a main data source or a dataview, they'll share the same data records. 
	- If you need to use a local data copy, u can create a local datasource from a main datasource by using `DataSourceManager.getInstance.createLocalDataSource()`
- Local data view: a local datasource created from a data view

# Select Datasource (Setting)
## Datasource Types: 
- Webmap

## Hàm chọn datasource

```js
const onDataSourceSelected = (useDataSources: UseDataSource[]) => {
	props.onSettingChange({ // Chuc nang tham so , .. 
		id: props.id,
		useDataSources: useDataSources,
	});
};
```

Sử dụng DatasourceSelector để chọn Datasource, với type là `Webmap`

```js
const supportedTypes = Immutable([AllDataSourceTypes.WebMap]);
return 
<DataSourceSelector
	types={supportedTypes} // 
	mustUseDataSource
	useDataSources={props.useDataSources}
	onChange={onDataSourceSelected}
	widgetId={props.id}
/>
```

### Reference
- [Git - Setting Datasource Selector WebMap](https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/create-map/src/setting/setting.tsx)
- [Git - Setting Datasource Selector FeartureLayer - FeatureService](https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/view-data-map/src/setting/setting.tsx)
