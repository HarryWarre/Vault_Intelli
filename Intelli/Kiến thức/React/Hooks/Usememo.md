Tags: #react #hooks
React Hook that lets you cache the result of a calculation between re-renders.
Link: 
Example:
```js
import { useMemo } from 'react';  
```

  

```js
function TodoList({ todos, tab, theme }) {  

const visibleTodos = useMemo(() => filterTodos(todos, tab), [todos, tab]);  

// ...  
````

Input:
You need to pass two things to `useMemo`:

1. A calculation function that takes no arguments, like `() =>`, and returns what you wanted to calculate.
2. A list of dependencies including every value within your component that’s used inside your calculation.

- **Khi nào sử dụng `useMemo`**:
    
    - Khi bạn có các phép tính phức tạp và muốn tránh tính toán lại mỗi khi component render.
    - Khi bạn muốn đảm bảo rằng một giá trị được nhớ và chỉ tính toán lại khi một trong các dependencies thay đổi.
- **Ví dụ thực tế**: Giả sử bạn có một danh sách lớn và cần tính tổng của các giá trị trong danh sách đó. Nếu không sử dụng `useMemo`, tổng sẽ được tính toán lại mỗi lần component render, điều này có thể làm chậm hiệu suất ứng dụng.