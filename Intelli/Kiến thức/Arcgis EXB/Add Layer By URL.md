Thêm một lớp layer vào map bằng cách thêm một URL

1. Thêm Map Widget, map được dùng để thêm Layer
- Có 2 components: 
	- Map Widget component
	- Add Layer Component
- Trong Add Layer Component, cần phải thêm map được chọn để thêm Layer

Code
```js
import { MapWidgetSelector } from 'jimu-ui/advanced/setting-components'

const onMapWidgetSelected = (useMapWidgetIds: string[]) => { 
	props.onSettingChange({ id: props.id, useMapWidgetIds: useMapWidgetIds 
}) }

return ( 
<div className="widget-setting-demo"> 
	<MapWidgetSelector useMapWidgetIds={props.useMapWidgetIds} onSelect={onMapWidgetSelected} /> 
</div> )
```


Trong phần code, sử dụng hàm `onMapWidgetSelected` để thực hiện chọn map dụa trên danh sách map

`MapWidgetSelector` được dùng dể chọn map

[Git Link](https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/add-layer/src/runtime/widget.tsx)

