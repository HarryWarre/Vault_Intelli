Tags: #react #usereducer #hooks 

# Introduce

- useReducer là một Hook React được sử dụng để quản lý trạng thái phức tạp hơn hoặc khi nhiều logic cập nhật trạng thái. Nó tương tự như `useState`, nhưng cung cấp một cách tiếp cận dựa trên reducer pattern thường được sử dụng như Redux

# Cú pháp

```js
const [state, dispatch] = useReducer(reducer, initialState);
```

- **`state`** là trạng thái hiện tại được lưu trong component
- **`dispatch`**: Là hàm dùng để gửi dispatch một action, giống như trong Redux
- reducer: Là một hàm quản lý cách trạng thái thay đổi dựa trên action
- initalState: Là trạng thái ban đầu của ứng dụng / component

# Cấu túc reducer function

- Reducer 2 tham số
	- state: Trạng thái hiện tại của ứng dụng
	- action: Một đối tượng chứa loại action và các dữ liệu cần thiết để cập nhật trạng thái
```js
function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}
```

# Khi nào cần sử dụng useReducer
1. Khi logic cập nhật phức tạp: Khi bạn có nhiều nhán khác nhau để cập nhật trạng thái (nhiều loại action), useReducer cung cấp một cách tổ chức dễ quả lý hơn so với `useState`
2. Khi trạng thái có nhiều phần tử phụ thuộc lẫn nhau: Trạng thái có cấu trúc phức tạp (object nhiều keys), useReducer sẽ gom lại 1 nơi
3. Khi muốn tách biệt logic cập nhật: Tách biệt logic cập nhật một hàm reducer và sử dụng lại nhiều nơi

```js
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
}

export default Counter;

```

## Ví dụ về quản lý nhiều state

```js
import React, { useReducer } from 'react';

const initialState = {
  username: '',
  email: '',
  password: ''
};

function formReducer(state, action) {
  switch (action.type) {
    case 'SET_USERNAME':
      return { ...state, username: action.payload };
    case 'SET_EMAIL':
      return { ...state, email: action.payload };
    case 'SET_PASSWORD':
      return { ...state, password: action.payload };
    default:
      return state;
  }
}

function SignupForm() {
  const [state, dispatch] = useReducer(formReducer, initialState);

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(state); // handle form submission
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        placeholder="Username"
        value={state.username}
        onChange={(e) => dispatch({ type: 'SET_USERNAME', payload: e.target.value })}
      />
      <input
        type="email"
        placeholder="Email"
        value={state.email}
        onChange={(e) => dispatch({ type: 'SET_EMAIL', payload: e.target.value })}
      />
      <input
        type="password"
        placeholder="Password"
        value={state.password}
        onChange={(e) => dispatch({ type: 'SET_PASSWORD', payload: e.target.value })}
      />
      <button type="submit">Submit</button>
    </form>
  );
}

export default SignupForm;

```

### So sánh `useReducer` và `useState`:

| **Tiêu chí**               | **useState**                          | **useReducer**                              |
| -------------------------- | ------------------------------------- | ------------------------------------------- |
| **Phù hợp với trạng thái** | Đơn giản, ít liên kết                 | Phức tạp, nhiều giá trị liên kết            |
| **Logic cập nhật**         | Trực tiếp, đơn giản                   | Tách biệt trong reducer, phức tạp hơn       |
| **Tối ưu hóa logic**       | Tối ưu cho cập nhật từng phần nhỏ     | Tối ưu khi có nhiều loại cập nhật khác nhau |
| **Sử dụng khi**            | Ít logic cập nhật, component đơn giản | Cần quản lý nhiều nhánh cập nhật phức tạp   |

### Tips khi sử dụng `useReducer`:

1. **Sử dụng khi có nhiều actions**: Khi trạng thái của bạn có nhiều cách để thay đổi (như form với nhiều trường, hay game logic)

2. **Tối ưu với middleware**: Giống như Redux, có thể mở rộng `useReducer` với các middleware (tự thêm vào), những tác vụ như logging, xử lý bất đồng bộ (async actions), hay bắt lỗi.

3. **Lazy initialization**: Nếu trạng thái ban đầu cần được tính toán (ví dụ từ một API hoặc một tính toán phức tạp), sử dụng lazy initialization để tránh tính toán lại trạng thái ban đầu khi component re-render.

```js
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

Ban đầu, trạng thái của bộ đếm sẽ được tính toán dựa trên một giá trị lớn thông qua phép tính tốn kém, nhưng chúng ta chỉ muốn tính toán khi component được render lần đầu.
```js
import React, { useReducer } from 'react';

// Reducer function
function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

// Hàm khởi tạo với phép tính phức tạp
function init(initialCount) {
  // Giả sử đây là một phép tính tốn kém (như API call, tính toán lớn)
  return { count: initialCount * 2 };
}

function Counter({ initialCount }) {
  // Sử dụng useReducer với lazy initialization
  const [state, dispatch] = useReducer(reducer, initialCount, init);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
}

export default function App() {
  return <Counter initialCount={5} />;
}

```

#### Ví dụ 2: Khởi tạo trạng thái với dữ liệu từ localStorage

Giả sử chúng ta muốn khởi tạo trạng thái của bộ đếm bằng giá trị được lưu trong `localStorage`, và chỉ cần lấy giá trị đó khi component được render lần đầu.

```js
import React, { useReducer } from 'react';

// Reducer function
function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

// Lazy initialization từ localStorage
function init() {
  const savedCount = localStorage.getItem('count');
  return { count: savedCount ? parseInt(savedCount) : 0 };
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, null, init);

  // Lưu giá trị count vào localStorage mỗi khi state thay đổi
  React.useEffect(() => {
    localStorage.setItem('count', state.count);
  }, [state.count]);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
}

export default function App() {
  return <Counter />;
}

```