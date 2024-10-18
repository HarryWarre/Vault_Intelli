Tags: #arcgis_exb 

# Giới thiệu
- Trong Arcgis, có nhiều loại **Layer** khác nhau như: 
	- FeatureLayer: Đại diện cho các đối tượng dịa lý như điểm, đường và đa giác
	- TileLayer: Đại diện cho các lớp gạch ảnh (raster) được tải từ máy chủ
	- ImageryLayer: Lớp ảnh viễn thám
	- SceneLayer: Dữ liệu 3D trong môi trường SceneView

# Cách thêm Layer vào một map

Các bước để thêm một **FeatureLayer** vào bản đồ trong Arcgis Experience Builder

1. Tạo Layer
2. Thêm Layer vào Mapview

## Chọn map để thêm Layer

#### Hàm chọn các mapwidgetIds 
Tags: #setting 
```js
const onMapWidgetSelected = (useMapWidgetIds: string[]) => {
    props.onSettingChange({
      id: props.id,
      useMapWidgetIds: useMapWidgetIds,
    });
  };
```
#### Sử dụng MapWidgetSelector để chọn Map

```tsx
<MapWidgetSelector
        useMapWidgetIds={props.useMapWidgetIds}
        onSelect={onMapWidgetSelected}
      />
```

