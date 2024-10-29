
- Phương thức `hitTest` của `view` (thường là đối tượng MapView hoặc SceneView)
- Được sử dụng để phát hiện các đối tượng đồ hoạt hoặc tính năng (features) tại vị trí con trỏ chuột hoặc khi người dùng tương tác với bản đồ. 
- Nó trả về kết quả về những gì đã chạm vào vị trí trên bản đồ, chẳng hạn như các graphics, đối tượng trên bản đồ hoặc đối tượng 3D

# Cách hoạt động của `hitTest` trong `JimuMapView`:

1. Gọi `hitTest`: Phương thức `hitTest` được gọi từ view của `jimuMapView`
	- Phương thức nhận một vị trí (thường là tọa độ của con trỏ (pointer) hoặc một sự kiện nhấp chuột (click event)) 
	- Phương thức trả về: Một Promise chứa thông tin về các đối tượng đồ họa hoặc tính năng (features) tại vị trí đó

2. Đầu vào
	- `event`: Một sử kiện chuột hoặc tọa độ của con trỏ. Thông thường, bạn sẽ lấy vị trí từ sự kiện nhấp chuột (click) hoặc sự kiện di chuyển chuột (pointer-move)
3.  Đầu ra
	- Kết quả trả về từ hitTest là một đối tượng (Object)  chứa thông tin về các đồ họa hoặc tính năng được phát hiện tại vị trí kiểm tra.


### Example
```js
jimuMapView.view.on("click", async (event) => {
const response = await jimuMapView.view.hitTest(event); 
if (response.results.length > 0) { 
const graphic = response.results[0].graphic; // Lấy đối tượng đồ họa đầu tiên 
console.log('Đồ họa được chọn:', graphic);// Bạn có thể xử lý đồ họa tại đây, ví dụ: hiển thị thông tin, phóng to, hoặc tương tác khác. } 
else { console.log("Không có đồ họa nào tại vị trí này."); }
});
```

### Giải thích
- **`jimuMapView.view.on("click", ...)`**: Sự kiện click trên bản đồ. Khi người dùng nhấp vào bản đồ,  thực hiện hành động kiểm tra xem có đồ họa nào tại vị trí được nhấp vào không.28/10
    
- **`view.hitTest(event)`**: Gọi phương thức `hitTest` trên view để kiểm tra các đối tượng tại vị trí mà người dùng nhấp vào (vị trí được lưu trong `event`).
    
- **`response.results`**: Một mảng chứa các đối tượng đồ họa hoặc tính năng được tìm thấy tại vị trí kiểm tra. Nếu có ít nhất một đối tượng, bạn có thể lấy đối tượng đó và xử lý theo nhu cầu (ví dụ: hiển thị popup, lấy thông tin chi tiết).


## Link về việc sử dụng hitTest
Đoạn code này sử dụng hitTest để thực hiện get được dữ liệu của rings (geometry của mảng polygon) từ đó đưa vào một function, function này sẽ thực hiện tạo một symbol simple-fill để tô màu và nhấp nháy mảng DMA được chọn

link: 
Function Blink Polygon:
https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/view-data-map/src/runtime/function.ts

Phần thực hiện hitTest
https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/view-data-map/src/runtime/widget.tsx#L383-L395