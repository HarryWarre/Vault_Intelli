Tags: #arcgis_exb #widget

# Widget
- Là thành phần giao diện trong Arcgis Experience builder
- Cung cấp các tính năng cụ thể

# Cấu trúc của một widget

- Widget.tsx: File chính cho thành phàn widget
- Setting.tsx: Thành phần quản lý cài đặt widget, cho phép cấu hình thuộc tính
- Manifest.json: Định nghĩa thông tin metadata (ID, tên, mô tả)
- Translation fiels: Tệp chưa các bản dịch để hỗ trợ đa ngôn ngữ

## Widget.tsx

```js
import { React } from 'jimu-core';
import { AllWidgetProps } from 'jimu-for-builder';

const Widget = (props: AllWidgetProps<any>) => {
  return (
    <div>
      <h3>{props.config.title || 'My Custom Widget'}</h3>
      {/* Nội dung của widget */}
    </div>
  );
};

export default Widget;
```

## Setting.tsx
- Thành phần chịu trách nhiệm cấu hình widget, cho phép tùy chỉnh như chọn Datasource, ...

```js
import { React } from 'jimu-core';
import { AllWidgetSettingProps } from 'jimu-for-builder';

const Setting = (props: AllWidgetSettingProps<any>) => {
  const onSettingChange = (title: string) => {
    props.onSettingChange({
      id: props.id,
      config: props.config.set('title', title),
    });
  };

  return (
    <div>
      <input 
        type="text" 
        value={props.config.title || ''} 
        onChange={e => onSettingChange(e.target.value)}
      />
    </div>
  );
};

export default Setting;
```

## Manifest.json

Tệp json định nghĩa cấu trúc và metadata của widget

```json
{
	"name": "create-map",
	"label": "create-map",
	"type": "widget",
	"dependency": ["jimu-arcgis"],
	"version": "1.14.0",
	"exbVersion": "1.14.0",
	"author": "Esri R&D Center Beijing",
	"description": "This is a barebones, simple widget. It includes an example of how to use the config file, and it includes a placeholder SVG icon. It intentionally does not include the following so you can use this to start from scratch: i18n translations, a Settings panel, unit tests. See the documentation for more information on how to implement these features.",
	"copyright": "",
	"license": "http://www.apache.org/licenses/LICENSE-2.0",
	"properties": {
		"canCreateMapView": true
		},
		"translatedLocales": ["en"],
		"defaultSize": {
		"width": 800,
		"height": 500
	}
}
```

