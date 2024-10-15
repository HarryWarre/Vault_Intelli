`memo` lets you skip re-rendering a component when its props are unchanged.

`const MemoizedComponent = memo(SomeComponent, arePropsEqual?)`


### Cách hoạt động:

1. **Bọc component**: Khi bạn bọc một component trong `memo`, React sẽ "nhớ" nó. Điều này có nghĩa là nếu component cha của nó render lại nhưng props của component không thay đổi, thì component đó sẽ không được render lại.
    
2. **So sánh props**: React sẽ so sánh props mới với props cũ. Nếu không có sự thay đổi, React sẽ sử dụng phiên bản đã "nhớ" và không thực hiện render lại. Tuy nhiên, nếu props thay đổi, component sẽ được render lại.
    

### Ví dụ dễ hiểu:

Giả sử bạn có một component đơn giản hiển thị tên người dùng:

`import { memo } from 'react';  const UserName = memo(function UserName({ name }) {   console.log("Rendering UserName");   return <div>{name}</div>; });`

#### Cách sử dụng:

`import React, { useState } from 'react'; import UserName from './UserName';  function App() {   const [count, setCount] = useState(0);   const [name, setName] = useState("John");    return (     <div>       <UserName name={name} />       <button onClick={() => setCount(count + 1)}>Increase Count</button>     </div>   ); }`

### Cách hoạt động:

- Khi bạn nhấn nút "Increase Count", `count` sẽ tăng lên, và component `App` sẽ được render lại.
- **Nhưng**: Component `UserName` sẽ **không** render lại vì props `name` của nó không thay đổi. Bạn sẽ thấy "Rendering UserName" **không** được in ra console lần nữa, tức là React đã sử dụng phiên bản đã "nhớ" của component.

### Tóm tắt:

- `React.memo` giúp cải thiện hiệu suất bằng cách tránh render lại những component không cần thiết.
- Nó không đảm bảo rằng component sẽ không bao giờ render lại, nhưng sẽ làm như vậy **khi** props không thay đổi.
- Đây là một cách đơn giản để tối ưu hóa các ứng dụng React của bạn, đặc biệt là khi có nhiều component phức tạp và bạn không muốn chúng render lại mà không cần thiết.

