Tags: #arcgis_exb #snap
Reference: [Snap in Arcgis EXB](https://developers.arcgis.com/javascript/latest/api-reference/esri-views-interactive-snapping-SnappingOptions.html)

# Giới thiệu

- Tính năng snap (bắt dính) giúp người dùng dễ dàng tương tác với bản đồ bằng cách tự động bắt (snap) con trỏ chuột hoặc đối tượng đến các vị trí chính xác trên bản đồ, chẳng hạn như các điểm, đường hoặc lưới. Tính năng được sử dụng chủ yếu khi bạn cần đảm bảo độ chính xác trong công việc hoặc di chuyển các đối tượng trên bản đồ

## Tình huống phổ biến khi sử dụng snap

- Khi vẽ các đối tượng như điểm, đường thẳng hoặc hình đa giác, snap giúp tự odonjg đưa con trỏ tới vị trí gần nhất, giúp vẽ chính xác hơn
- Trong quá trình chỉnh sửa các đối tượng trên map, snap có thể giúp canh chỉnh các đối tượng với nhau hoặc với cá đặc điểm trên bản đồ

## Measure Map setting

- Là công cụ đo lường để đo diện tích và khoảng cách. Đo lường sử dụng `snap` để bắt điểm - con trỏ bắt điểm vào các đối tượng trên bản đồ. Khi đó, người dùng có thể nhấn và giữ phím `Ctrl` để tạm thời tắt tính năng `snap`

## Cách kích hoạt snap 
- Khi làm việc với bản đồ trong arcgis, bạn có thể bật hoặc tắt tính năng snap thông qua **cài đặt** ( trong map thì snap là measure)

Snap thường rất hữu ích khi người dùng cần đảm bảo rằng các đối tượng trên bản đồ được căn chỉnh và định vị chính xác so với các đặc điểm khác.


# Snap Options

The `SnappingOptions` allows users to configure snapping for their editing or drawing experience in both the [Sketch](https://developers.arcgis.com/javascript/latest/api-reference/esri-widgets-Sketch.html#snappingOptions) and [Editor](https://developers.arcgis.com/javascript/latest/api-reference/esri-widgets-Editor.html#snappingOptions) widgets.

## Self snapping (Geometry guides)

- Được thiết lập thông qua selfEnabled, tính năng giúp người dùng dễ dàng tạo và cập nhật đối tượng bằng cách hiển thị các hướng dẫn hình học (geometry guide). 
- Hệ thống sẽ cung cấp các hướng dẫn trực quan cho người dùng
	- Căn chỉnh các đường thẳng song song và vuông góc
	- Bám vào phầm mở rộng của đối tượng hiện có

![](https://developers.arcgis.com/javascript/latest/assets/img/apiref/widgets/sketch/snapping-self-2d.gif)

## Feature snapping

 - Tính năng giúp người dùng bám dính (snap) các đỉnh, cạnh hoặc điểm cuối của đối tượng hiện tại với các đặc điểm tương tự với các đối tượng sẵn. 
 - Thông qua thuộc tính `featureEnabled` Và các đối tượng mà bạn muốn snap tới phải được xác định trong thuộc tính `featureSources`
 - Cụ thể có 2 tính năng chính
	 - Snap khi tạo đối tượng mới: Khi tạo một đối tượng mới, đỉnh hoặc cạnh của đối tượng có thể tự động bám dính các định, cạnh  hoặc đỉnh cuối của đối tượng đã có trong bản đồ
	 - Snap khi chỉnh sửa đối tượng hiện tại: Khi thay đổi hình dạng của một đối tượng, các đỉnh của nó có thể snap vào các đỉnh đối tượng khác để tạo sự kết nối chính xác
![](https://developers.arcgis.com/javascript/latest/assets/img/apiref/widgets/sketch/snapping-feature-2d.gif)
![](https://developers.arcgis.com/javascript/latest/assets/img/apiref/widgets/sketch/snapping-reshape-2d.gif)

# Pointer-up Snap

- Là hành vi khi thực hiện thao tác với con trỏ. Khi người dùng thả con trỏ  (khi thực hiện Pointer-up) đối tượng hoặc hình học à họ đang thao tác sẽ bắt dính (snap) vào một điểm chính xác gần nhất trên **map**

## Cách hoạt động của Pointer up Snap:

1. Pointer-up là hành động xảy ra khi thả nút chuột hoặc tạm dừng chạm vào màn hình cảm ứng sau khi duy chuyển hoặc vẽ một đối tượng
2. Snap giúp tự động căn chỉnh đối tượng tới điểm gần nhất hoặc phù hợp với các yếu tố địa lý hoặc lưới đã được định sẵn trên bản đồ
3. Pointer-up snapping có thể diễn ra đối với các điểm, đường hoặc các hình học khác mà hệ thống cho phép bắt dính

## Tình huống sử dụng Pointer-up

1. Vẽ đối tượng trên bản đồ: bao gồm đường hoặc hình đa giác
2. Chỉnh sửa hình học: Di chuyển một đỉnh hoặc đoạn của hình đa giác, saui khi thả chuột, đỉnh đó có thể snap vào một vị trí gần nhất, giúp căn chỉnh nhanh chóng và chính xác 

## Tại sao snap pointer-up lại quan trọng
- Độ chính xác cao hơn: Giúp người dùng thao tác chính xác hơn mà không cần điều chỉnh thủ công
- Tự động căn chỉnh: Hữu ích khi map có nhiều đối tượng
- Tăng tốc thao tác

## Reference: 
- [[Draw Widget]]
- [Access pointer with features event](https://developers.arcgis.com/javascript/latest/sample-code/view-hittest/)
