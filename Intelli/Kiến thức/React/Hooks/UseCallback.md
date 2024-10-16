Tags: #react #usecallback #hooks

Reference: [W3 - UseCallback](https://www.w3schools.com/react/react_usecallback.asp)

# Introduce

The react **`useCallback`** Hook returns a memoized callback function

- Usecallback được sử dụng để ghi nhớ (memoize) một hàm và chỉ tạo lại hàm đó khi một hoặc nhiều giá trị trong mảng dependencies thay đổi
- Giúp tối ưu hóa hiệu suất ứng dụng

## Cú pháp 

```js
const memoizedCallback = useCallback(
  () => {
  },
  [dependency1, dependency2] // mảng dependencies
);

```

## Khi nào nên dùng useCallback

1. Tránh tạo lại hàm không cần thiết: Một hàm được truyền xuống dưới các component con dưới dạng props, nếu hàm đó thay đổi, components con sẽ re-render lại dù props khác không thay đổi
	- usecallback giúp ngăn điều này bằng cách ghi nhớ phiên bản trước của hàm nếu dependecies không thay đổi
2. Giảm chi phí tái tạo hàm: Khi một component re-render, cá hàm được định nghĩa trong component sẽ được tái tạo lại . 
	- useCallback giúp ghi nhớ hàm để tránh tính toán lại mỗi lần re-render

```js
const ParentComponent = () => {
  const [count, setCount] = useState(0);

  // Hàm này sẽ không thay đổi trừ khi `count` thay đổi
  const increment = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return <ChildComponent increment={increment} />;
};

const ChildComponent = React.memo(({ increment }) => {
  console.log("Child rendered");
  return <button onClick={increment}>Increment</button>;
});
```
Nếu không sử dụng useCallback , hàm increment  tạo lại mỗi lần ParentComponent render, và ChildComponent sẽ render lại mỗi lần ngay cả khi count không thay đổi 


# Cách hoạt động của useCallback

1. Memoization của callback
- Mỗi lần re-render, React sẽ kiểm tra dependencies ? 
	- Tạo hàm mới 
	- Trả về phiên bản hàm đã ghi nhớ từ trước, giúp tránh tạo ra một hàm mới
2. Phụ thuộc vào mảng dependencies
3. Chú ý về so sánh nông (shallow comparion)
- Nếu truyền vào một object thì nó vẫn sẽ render bất kể có giống hay không
4. Không ngăn re-render hoàn toàn
- useCallback chỉ đảm bảo rằng hàm callBack không thay đổi nếu dependencies không thay đổi 

# Khi nào không nen sử dụng useCallback

1. Hàm callback đơn giản hoặc không tốn tài nguyên. Nếu callback đơn giản thì sử dụng useCallback có thể gây tốn tài nguyên
2. Dependencies phức tạp: nhiều dependencies tahy đổi thường xuyên, việc sử dụng useCallback có thể không thực sự hiệu quả vì hàm callback luôn tại lại một khi dependency thay đổi
3. Không có ảnh hưởng hiệu suất rõ ràng: Nếu việc tạo lại hàm không gây ra re-render không cần thiết hoặc gây ảnh hưởng đến hiệu suất tổng thể thì không cần dùng

# useMemo và useCallback
- Điểm tương đồng giữa useCalback và useMemo là cả 2 đều memoized kết quả dựa trên dependencies
	- `useCallback` memoize một hàm
	- `useMemo` memoize một giá trị tính toán
Note: Nếu bạn thấy có thể sử dụng useCallback để  memoize một hàm trả về một giá trị, bạn có thể sử dụng `useMemo` để thay thế