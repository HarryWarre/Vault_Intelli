Tags: #arcgis_exb 
Reference: 
# Giới thiệu
- Là một lớp quản lý bản đồ trong Jimu framework, giúp các widget tương tác với bản đồ và quản lý với các chức năng bản đồ, view, geo-data, extent

Trong jimumapview, có thể tạo, quản lý và điều khiển các phiên bản bản đồ (MapView / SceneView) sử dụng chúng trong các widget của ArcGIS EXB

1. JimuMapViewManager: 
	- Là lớp quản lý, JimuMapVIew. Cho phép tạo hoặc truy cập JimuMapView đã tồn tại, đồng bộ trạng thái bản đồ giữa các widgets
2. JimuMapView: 
	- Là một đối tượng đại diện cho một bản đồ đang hiển thị (MapView) hoặc SceneView
3. createJimuMapView
	- Phương thức này của `MapViewManager` để tạo một JimuMapView mới dựa trên MapView/SceneView đã được định nghĩa trong widget
4. Interaction between WIdgets and Map:
	- JimuMapView cho phép các widget trong ứng dụng tương tác với bản đồ


## 