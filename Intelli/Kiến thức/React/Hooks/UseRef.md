Tags: #react #hooks 
# Introduce
- useRef is a React Hook that lets you reference a value that's not needed for rendering

```js
const ref = useRef(initialValue)
```

# Reference
Call `useRef` at the top level of your component to declare a ref.

```js
import { useRef } from 'react';  

function MyComponent() {  
	const intervalRef = useRef(0);  
	
	const inputRef = useRef(null);  
// ...
```

