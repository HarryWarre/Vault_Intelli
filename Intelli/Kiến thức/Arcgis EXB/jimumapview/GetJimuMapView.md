```js
export async function getJimuMapView(

mapWidgetId: string,
_viewManager: MapViewManager
) {

const activeViewId = _getActiveViewId(
mapWidgetId,
getAppStore().getState().jimuMapViewsInfo

);

const jimuMapView: JimuMapView =
_viewManager.getJimuMapViewById(activeViewId);
return await jimuMapView?.whenJimuMapViewLoaded();
}
```