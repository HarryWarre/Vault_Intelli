Tags: #react #hooks
# Introduce
- `useEffect` is a React Hook that lets you [synchronize a component with an external system.](https://react.dev/learn/synchronizing-with-effects)
- `Hooks đồng bộ dữ liệu khi có sự thay đổi`

- Ví dụ: 
```js
useEffect(setup, dependencies?)
```


# Reference
- Call useEffect **at the top level** of your component to declare an Effect

```js
import { useEffect } from 'react';  

import { createConnection } from './chat.js';  

function ChatRoom({ roomId }) {  

const [serverUrl, setServerUrl] = useState('https://localhost:1234'); 
  

useEffect(() => {  

	const connection = createConnection(serverUrl, roomId);  

	connection.connect();  

	return () => {  
		connection.disconnect();  
	};  

}, [serverUrl, roomId]);  

// ...  
}
```

Giải thích
- Khi serverUrl hoặc roomId thay đổi thì nó thực hiện lại hàm useEffect trên
- Chỉ được gọi ở trên đầu components hoặc hooks
