Tags: #react #memo #usememo #useCallback

So sánh usememo và react memo
1. [[Usememo]]
2. [[memo]]

Ref: https://viblo.asia/p/react-memo-va-usememo-aWj534z1K6m

1.	React memo
-	React memo sinh ra với mục đích tránh việc rerender nhiều lần ảnh hưởng đến hiệu năng
1. const MyComponent = React.memo(function MyComponent(props) {
2.   /* only rerenders if props change */
3. });
4.  
Ví dụ về react memo
 ```js
 0. const Child = React.memo(props => {
 1.   console.log("rendered");
 2.   return <React.Fragment>{props.name}</React.Fragment>;
 3. });
 4.  
 5. class App extends React.Component {
 6.   state = {
 7.     value: 1,
 8.     name: "Jioke"
2.   };
3.  
4.   handleClick = () => {
5.     this.setState({
6.       value: this.state.value + 1
7.     });
8.   };
9.  
10.   render() {
11.     return (
12.       <React.Fragment>
13.         <Child name={this.state.name} />
14.         <div>{this.state.value}</div>
15.         <button onClick={this.handleClick}>+</button>
16.       </React.Fragment>
17.     );
18.   }
19. }
20.  
```

-	Component child đang bao là một react memo, như vậy có tác dụng:
o	Thứ nhất, nó nhận prop là name truyền từ component App, bình thường mỗi lần click button value +1. Và tất cả được rerender được update lại DOM để chúng ta có thể nhìn thấy sự thay đổi
o	Thứ 2, nếu có memo khi nhấn click button chỉ có giá trị value thay đổi, name không đổi và được truyền vào component Child. vì có memo nên nó sẽ check prop chuyền vào có thay đổi không, nếu thay đổi chúng sẽ rerender, còn không thay đổi sẽ không cần làm gì
o	Mỗi lần click button thì component Child không hề được render lại, chúng ta chỉ thấy console chỉ 1 lần duy nhất rerender

[Codepen](https://codepen.io/kinsomicrote/pen/JwOoej?editors=1111)

2.	Usememo
-	useMemo cũng giống với khái niệm React memo, nhưng có sự khác biệt rõ ràng.
-	Nếu như react memo sinh ra với mục đích tránh việc rerender nhiều lần thì useMemo tránh việc tính toán lại một function nhiều lần mỗi khi một component rerender
-	Bản chất useMemo là caching lại giá trị return của function, mỗi lần component rerender nó sẽ kiểm tra lại giá trị tham số truyền vào function nếu giá trị đó không thay đổi, thì return value đã caching trong memory. 
-	Ngược lại, nếu giá trị tham số truyền vào thay đổi, nó sẽ thực hiện tính toán lại và caching vào memory cho những lần rerender tiếp theo
```js
1. const memoizedValue = useMemo(
2. () => computeExpensiveValue(a, b), [a, b]);
3.  
```

a,b là 2 tham số truyền vào useMemo để tối ưu cho tính toán khi component re-render
Trong react Memo tham số nó là props chuyền vào cho Child component.

 ```js
 1. import React, { useState, useMemo } from "react";
 2. import ReactDOM from "react-dom";
 3.  
 4. function App() {
 5.  
 6.   const [count, setCount] = useState(0);
```
