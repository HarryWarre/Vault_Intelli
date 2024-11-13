# Đặc điểm của React
<p align="justify">JSX: Là phần mở rộng của cú pháp Javascript. Bằng cách sử dụng JSX, chúng ta có thể viết các cấu trúc HTML trong cùng một tệp chứa code JavaScript</p>
- Components: chia giao diện thành các phần độc lập, có thể tái sử dụng và xử lý riêng

- Dom ảo (Virtual Dom): nhẹ hơn Dom thực, khi trạng thái đối tượng thay đổi, Dom ảo sẽ cập nhật đối tượng đó trong Dom thật thay vì cập nhật toàn bộ đối tượng

- Oneway data binding: Truyền dữ liệu một chiều, lồng các components con trong component mẹ

- Hiệu suất: Chỉ cập nhật các components đã thay đổi thay vì cập nhật toàn bộ. Giúp web nhanh hơn đáng kể

# Jsx là gì ?
- Là phần mở rộng cho cú pháp Javascript. JSX được sử dụng để có thể viết cấu trúc javascript trong HTML

# Các trình duyệt có thể đọc JSX trực tiếp không ?
- Các trình duyệt không thể đọc JSX trực tiếp vì nó được xây dựng để đọc các đối tượng JS thông thường, không phải JSX
- Để có thể đọc được JSX, nó sẽ chuyển đổi sang JS thông thường thông qua **Babel**

# Dom ảo là gì ?

- Viết tắt của Document Object Model.
- Đại diện cho một tài liệu của HTML có cấu trúc cây logic. Mỗi nhánh của cây kết thúc bằng một nút và mỗi nút chứa các đối tượng

![DOM ảo - Virtual DOM là gì](https://itviec.com/blog/wp-content/uploads/2021/12/reactjs-la-gi-cau-hoi-phong-van-30.jpg)

React sẽ giữ một bản đại diện, nhưng nhẹ hơn DOM thực trong bộ nhớ, gọi là DOM ảo. Khi trạng thái của đối tượng thay đổi, DOM ảo sẽ cập nhật lại đối tượng đó trong DOM thực.

# Ưu điểm của React thay vì framework khác, ví dụ Angular

- Dễ dàng tạo các ứng dụng động
	- React giúp tạo các ứng dụng web động dễ dàng ít code hơn mà lại cung cấp nhiều chức năng. Trong khi các ứng dụng Javascript khác thường có xu hướng trở nên phức tạp
- Hiệu suất cải thiện: React sử dụng DOM ảo, giúp chỉ cập nhật các đối tượng có trạng thái thay đổi thay vì toàn bộ
- Các thành phần có thể tái sử dụng 
	- Là nền tảng của bất kỳ ứng dụng Reac nào. Có thể tái sử dụng
- One-way Binding : Luồng dữ liệu 1 chiều giúp dễ dàng debug hơn

# Sự khác nhau giữa ES6 và ES5

- Components và Function
![es5 - es6 - components và function](https://itviec.com/blog/wp-content/uploads/2021/12/reactjs-la-gi-cau-hoi-phong-van-1.jpg)

- exports vs export
- require vs import
```js
//ES5
var React = require('react')
//ES6
import React from 'react'
```

# Sự kiện (Event) trong React là gì
Là hành động mà người dùng có thể hành động như click, ...
- Các sự kiện React được đặt tên dựa trên CamelCase
- Với JSX, hàm được dùng cho xử lý sự kiện thay vì chuỗi trong HTML


# Sự kiện tổng hợp là gì (Synthetic event)

- Sự kiện tổng hợp (Synthetic event) kết hợp phản hồi của các sự kiện gốc của trình duyệt khác nhau thành một API, đảm bảo rằng các sự kiện nhất quán trên các trình duyệt khác nhau.
- Là lớp bọc xung quanh sự kiện của trình duyệt, giúp các sự kiện hoạt động đồng nhất trên mọi trình duyệt 
	- **Đồng nhất giữa các trình duyệt**: Synthetic Event giúp các sự kiện React như `onClick`, `onChange` hoạt động giống nhau trên mọi trình duyệt.
	- **Tối ưu hiệu suất**: React dùng một listener chung cho các sự kiện, thay vì gắn từng listener cho từng phần tử, giúp giảm tải bộ nhớ.
	- **Quản lý bộ nhớ**: Sự kiện sẽ tự giải phóng bộ nhớ khi xong việc, nên tiết kiệm tài nguyên hơn.
	Ví dụ, khi bạn thêm `onClick` vào một nút trong React, bạn đang làm việc với Synthetic Event, chứ không phải sự kiện gốc của trình duyệt.

# Vì sao sử dụng key trong danh sách
Key rất quan trọng trong danh sách bởi vì:
- key là độc nhất, được sử dụng để xác định mục nào thay đổi, xóa, hay cập nhật
- Giúp xác định thành phần nào được render 

# Arrow function
- một cách viết ngắn gọn của một hàm trong React.
- Không cần thiết phải ràng buộc ‘this’ bên trong phương thức khởi tạo khi sử dụng hàm mũi tên. Điều này ngăn chặn các bug do sử dụng ‘this’ trong các lệnh Callback trong React
![hàm mũi tên react - arrow function reactjs](https://itviec.com/blog/wp-content/uploads/2021/12/reactjs-la-gi-cau-hoi-phong-van-11.jpg)


### Điểm khác nhau giữa React và React Native?

|                   | **React**             | **React Native**      |
| ----------------- | --------------------- | --------------------- |
| **Năm phát hành** | 2013                  | 2015                  |
| **Nền tảng**      | Web                   | Mobile – Android, iOS |
| **HTML**          | Có                    | Không                 |
| **CSS**           | Có                    | Không                 |
| **Yêu cầu**       | JavaScript, HTML, CSS | React.js              |

### Điểm khác nhau giữa React và Angular?

|                      | **Angular**           | **React**            |
| -------------------- | --------------------- | -------------------- |
| **Tác giả**          | Google                | Facebook             |
| **Mô hình**          | Mô hình MVC toàn diện | Các lớp (layer) MVC  |
| **DOM**              | DOM thực              | DOM ảo (Virtual DOM) |
| **Liên kết dữ liệu** | Hai chiều             | Đơn chiều            |
| **Rendering**        | **Client-Side**       | **Server-Side**      |
| **Hiệu suất**        | Khá chậm              | Nhanh hơn nhờ DOM ảo |

# Component trong React
Có hai loại component trong React:

**Functional Components:** Loại components này không có state của riêng chúng và chỉ chứa các phương thức render, do đó còn được gọi là **stateless components**.

Chúng có thể lấy dữ liệu từ các components khác làm props (properties – thuộc tính).

```js
function Greeting(props) {  
return <h1>Welcome to {props.name}</h1>;  
}
```


- **Class Components:** Loại components này có thể giữ và quản lý state của riêng chúng và có một phương thức render riêng để trả về JSX trên màn hình. Chúng cũng được gọi là **stateful components** vì chúng có thể có một state.

```js
class Greeting extends React.Component {  
render() {  
  return <h1>Welcome to {this.props.name}</h1>;  
 }  
}
```

# Cách sử dụng hàm render() trong React

![hàm render() react - render() function reactjs](https://itviec.com/blog/wp-content/uploads/2021/12/reactjs-la-gi-cau-hoi-phong-van-12.jpg)


### State trong React là gì?

- State là một đối tượng (object) React tích hợp được sử dụng để chứa dữ liệu hoặc thông tin về component. State trong một component có thể thay đổi theo thời gian và bất cứ khi nào nó thay đổi, component sẽ render lại.

- Sự thay đổi state có thể xảy ra dưới dạng phản hồi đối với hành động của người dùng hoặc các sự kiện do hệ thống tạo. State xác định hành vi của component và cách component sẽ render.

# Props trong React là gì 
- là viết tắt của từ Properties. Đây là một đối tượng tích hợp trong React, lưu trữ giá trị của các thuộc tính của tag và hoạt động tương tự như các thuộc tính HTML.

- Props cung cấp cách để truyền dữ liệu từ component này sang component khác. 
- Các props được truyền cho component theo cách giống như các arguments được truyền trong một hàm.


### Điểm khác nhau giữa State và Props?

|                                    | **State**                        | **Props**                                                                        |
| ---------------------------------- | -------------------------------- | -------------------------------------------------------------------------------- |
| **Cách dùng**                      | Chứa dữ liệu về components       | Cho phép truyền dữ liệu từ component sang những components khác như một argument |
| **Khả năng thay đổi (Mutability)** | Có thể thay đổi                  | Không thể thay đổi                                                               |
| **Chỉ đọc (Read-Only)**            | Có thể thay đổi                  | Là read-only                                                                     |
| **Component con**                  | Component con không thể truy cập | Component con có thể truy cập                                                    |
| **Stateless components**           | Không thể có state               | Có thể có props                                                                  |

### Higher-order component (HOC) trong React là gì?

Higher-order component (HOC) hoạt động như một thùng chứa cho các components khác. Điều này giúp giữ cho các components “gọn gàng” và sẵn sàng tái sử dụng. HOC thường được sử dụng khi nhiều components phải sử dụng một logic chung.

#  Làm thế nào để nhúng hai hoặc nhiều component thành một?

Đưa 2 component vào một component chung
# Điểm khác nhau giữa Class components và Functional components?

|                          | **Class Components**                          | **Functional Components**                    |
| ------------------------ | --------------------------------------------- | -------------------------------------------- |
| **State**                | Có thể giữ hoặc quản lý state                 | Không thể giữ hoặc quản lý state             |
| **Độ đơn giản**          | Phức tạp hơn so với stateless component       | Đơn giản và dễ hiểu                          |
| **Lifecycle methods**    | Có thể hoạt động với tất cả lifecycle methods | Không thể hoạt động với lifecycle method nào |
| **Khả năng tái sử dụng** | Có thể                                        | Không thể                                    |

# Giải thích lifecycle methods của components

- **getInitialState()**: Hàm này diễn ra trước khi tạo component.
- **componentDidMount()**: Diễn ra khi component được render và đặt trong DOM.
- **shouldComponentUpdate()**: Được kích hoạt khi một component xác định các thay đổi với DOM và trả về giá trị “true” hoặc “false” dựa trên những điều kiện nhất định.
- **componentDidUpdate()**: Được kích hoạt ngay lập tức sau khi render.
- **componentWillUnmount()**: Được kích hoạt ngay lập tức trước khi một component bị hủy và tháo vĩnh viễn.

# Redux là gì?

một thư viện JavaScript mở được dùng để quản lý trạng thái ứng dụng. React sử dụng Redux để xây dựng giao diện người dùng. Đây là vùng chứa trạng thái có thể dự đoán được cho các ứng dụng JavaScript và được sử dụng để quản lý trạng thái của toàn bộ ứng dụng.


## Các components của Redux là gì?

- **Store**: Giữ các state của ứng dụng.
- **Action**: Nguồn thông tin của store.
- **Reducer**: Xác định cách mà state của ứng dụng thay đổi theo các hành động được gửi đến store.

## Flux là gì?

- Flux là kiến trúc phần mềm mà Facebook dùng để xây dựng các ứng dụng web. Đây là một phương pháp xử lý dữ liệu phức tạp bên trong ứng dụng phía máy khách và quản lý các chiều dữ liệu trong ứng dụng React.

- Có một nguồn dữ liệu duy nhất (store) và việc kích hoạt các hành động nhất định là cách duy nhất để cập nhật chúng. Action gọi dispatcher, và sau đó cửa hàng được kích hoạt và cập nhật dữ liệu của riêng chúng sao cho phù hợp.

![flux là gì - reactjs redux](https://itviec.com/blog/wp-content/uploads/2021/12/reactjs-la-gi-cau-hoi-phong-van-19.jpg)

- Khi một dispatch đã được kích hoạt và store cập nhật, nó sẽ phát ra một sự kiện thay đổi mà các chế độ xem có thể render tương ứng theo đó.

## 34. Điểm khác nhau giữa Redux và Flux?

|     | **Redux**                                                                             | **Flux**                                                    |
| --- | ------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| 1.  | Redux là thư viện mã nguồn mở của JavaScript được dùng để quản lý trạng thái ứng dụng | Flux là một kiến trúc, không phải là framework hay thư viện |
| 2.  | Trạng thái của store là bất biến                                                      | Trạng thái của store là tùy biến                            |
| 3.  | Chỉ có thể có một store                                                               | Có thể có nhiều store                                       |
| 4.  | Sử dụng reducer                                                                       | Sử dụng dispatcher                                          |

### React Router là gì?

React Router là một thư viện định tuyến được xây dựng lên trên React, được dùng để tạo ra các tuyến trong một ứng dụng React.

## Vì sao ta cần sử dụng React Router?

- React Router duy trì sự nhất quán của cấu trúc và hành vi và được sử dụng để phát triển các ứng dụng **web single-page**.
- React Router cho phép nhiều chế độ xem trong một ứng dụng bằng cách xác định nhiều tuyến trong ứng dụng React.

## Định tuyến React (React routing) khác như thế nào so với định tuyến quy ước (conventional routing)?

|     | **Định tuyến React**                                      | **Định tuyến quy ước**                             |
| --- | --------------------------------------------------------- | -------------------------------------------------- |
| 1.  | Trang HTML đơn                                            | Mỗi view là một tệp HTML mới                       |
| 2.  | Người dùng điều hướng nhiều chế độ xem trong cùng một tệp | Người dùng điều hướng nhiều tệp cho mỗi chế độ xem |
| 3.  | Trang không làm mới vì nó là một tệp duy nhất             | Trang làm mới mỗi khi người dùng điều hướng        |
| 4.  | Cải thiện hiệu suất                                       | Hiệu suất chậm hơn                                 |

## Triển khai React routing
![react routing](https://itviec.com/blog/wp-content/uploads/2021/12/reactjs-la-gi-cau-hoi-phong-van-22.jpg)

# style components trong React?

- **Inline Styling**

![reactjs styling - Inline Styling](https://itviec.com/blog/wp-content/uploads/2021/12/reactjs-la-gi-cau-hoi-phong-van-23.jpg)

- **JavaScript Object**

![reactjs styling - JavaScript Object](https://itviec.com/blog/wp-content/uploads/2021/12/reactjs-la-gi-cau-hoi-phong-van-24.jpg)

- **CSS Stylesheet**

![reactjs styling - CSS Stylesheet](https://itviec.com/blog/wp-content/uploads/2021/12/reactjs-la-gi-cau-hoi-phong-van-25.jpg)