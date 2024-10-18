Tags: #react #hooks #usecontext 

Reference: [React - useContext](https://react.dev/reference/react/useContext)

# Tổng quan
 - `useContext` là một hook trong React cho phép bạn đọc và đăng ký nhận thông tin từ context mà bạn đã tạo ra bằng cách sử dụng `createContext`. 
 - Điều này giúp bạn truyền dữ liệu qua cây component mà không cần phải truyền props qua từng cấp độ.

```js
import { useContext } from 'react';  

  

function MyComponent() {  

const theme = useContext(ThemeContext);  

// ...
```

## Tham số
- **SomeContext**: Là context mà bạn đã tạo bằng `createContext`
- The context itself does not hold the **information**, it only represents the kind of information you can provide or read from components.

## Giá trị trả về

- `useContext(SomeContext)` Trả về giá trị hiện tại của context, giá trị này được xác định bởi componet cha gần nhất
	- Sử dụng `SomeContext.Provider`.
- Nếu không có Provider, giá trị mặc định được xác định khi tạo context sẽ được sử dụng

## Cảnh báo
- Chỉ sử dụng trong hàm component: `useContext` chỉ nên được gọi từ bên trong hàm component React hoặc từ custom hooks
- Tái sử dụng component: Nếu bạn gọi một component nhiều lần trong một cây component, mỗi lần sử dụng sẽ nhận được cùng một giá trị từ context

## Cách sử dụng useContext

```js 
import React, { createContext, useContext } from 'react';

// Tạo context
const ThemeContext = createContext('light'); // Giá trị mặc định là 'light'

function ThemedComponent() {
  // Sử dụng useContext để lấy giá trị từ ThemeContext
  const theme = useContext(ThemeContext);
  return <div style={{ background: theme === 'dark' ? '#333' : '#fff' }}>Hello, Theme!</div>;
}

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedComponent />
    </ThemeContext.Provider>
  );
}

export default App;

```


## Cập nhật dữ liệu thông qua Context

```js
import React, { createContext, useContext } from 'react';

// Tạo context
const ThemeContext = createContext('light'); // Giá trị mặc định là 'light'

function ThemedComponent() {
  // Sử dụng useContext để lấy giá trị từ ThemeContext
  const theme = useContext(ThemeContext);
  return <div style={{ background: theme === 'dark' ? '#333' : '#fff' }}>Hello, Theme!</div>;
}

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedComponent />
    </ThemeContext.Provider>
  );
}

export default App;

```

## Chỉ định giá trị mặc định

Khi bạn tạo context, bạn có thể chỉ định mọt giá trị mặc định. Ví dụ:

`const MyContext = createContext(defaultValue);

## Ghi đè context cho một phần của cây
Bạn có thể ghi đè giá trị của contexxt cho một phần của cây sử dụng Provider

```js
<SomeContext.Provider value={newValue}>
  {/* components here */}
</SomeContext.Provider>
```

## Tối ưu hóa re-renders

Khi truyền các đối tượng và hàm qua context, React có thể tái tạo lại các component tiêu thụ context khi giá trị đó thay đổi, dẫn đến render lại không cần thiết. Bạn có thể sử dụng `useMemo` hoặc `useCallback` để tối ưu hóa việc truyền các giá trị này. 1h30-14

`const value = useMemo(() => ({ count, increment }), [count]);`