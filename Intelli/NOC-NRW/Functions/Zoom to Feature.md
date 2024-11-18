Function: zoomToFeature

Input: detailDMA

Cách hoạt động
[[GetJimuMapView]]
```js
const jMapView = await getJimuMapView(mapWidgetId, _viewManager.current);
```

Tạo feature Layer:
`const featureLayer = createFeatureLayer(layerNRWUrl.DMA_NRW);`
Query Params:
```js
const query = featureLayer.createQuery();
query.where = `idDMA = '${detailDMA.idDMA}' and profileId = '${detailDMA.profileId}'`;
query.returnGeometry = true;
```

- Từ result query, lấy được feature:
```js
const feature = results.features[0];
```

Thực hiện thao tác trên jimumapview:
```js
jMapView.view.popup.dockEnabled = true; // Enable docking
	jMapView.view.popup.dockOptions = {
	  // Define docking options here
	  position: "top-left",
	  breakpoint: false,
	  buttonEnabled: false,
	};

	// zoom + show popup
	jMapView?.view
	  ?.goTo({ target: feature.geometry, zoom: 17 })
	  .then(() => {
		jMapView?.view?.openPopup({
		  title: `DMA - ${feature.attributes.ID_DMA}`,
		  content: getPopupContent(detailDMA),
		});
		// add graphic here
		showAreaOnMap(jMapView, feature.geometry as Polygon, true);
  });
}```