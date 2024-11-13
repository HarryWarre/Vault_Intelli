**Single or Multiple state ?**

# Single State
```js
const [x, setX] = useState(0);  
const [y, setY] = useState(0);
```
# Multiple State

```js
const [position, setPosition] = useState({ x: 0, y: 0 });
```

- Về mặt kĩ thuật, có thể dùng 1 trong 2 cách trên. Nhưng nếu 2 state luôn được thay đổi cùng nhau (có mối quan hệ chặt chẽ) thì nên dùng một State duy nhất (Multiple State)

Ví dụ về sự thay đổi cùng lúc cho 2 biến trên
```js
const [position, setPosition] = useState({
    x: 0,
    y: 0
  });
  return (
    <div
      onPointerMove={e => {
        setPosition({
          x: e.clientX,
          y: e.clientY
        });
      }}
```

Trong trường hợp khác, nếu bạn không biết được có bao nhiêu state bạn cần thì có thể chuyển nó thành một object hoặc array để sử dụng 

```js
setPosition({ ...position, x: 100 })
```

## Tránh mâu thuẫn state

Trong một số trường hợp, thay vì sử dụng nhiều state cho nhiều trạng thái, có thể gom lại thành một để tránh bị mâu thuẫn

VD: 

Một hành động trong 1 thời điểm chỉ có một trạng thái, và việc tạo 2 state cho nó là dư thừa
```js
 const [isSending, setIsSending] = useState(false);
  const [isSent, setIsSent] = useState(false);
```

Thay vào đó
```js
const [status, setStatus] = useState('typing');

  async function handleSubmit(e) {
    e.preventDefault();
    setStatus('sending');
    await sendMessage(text);
    setStatus('sent');
  }

  const isSending = status === 'sending';
  const isSent = status === 'sent';
```

## Tránh lồng state

Một state không nên được lồng quá nhiều, điều này dễ gây phức tạo trong việc lập trình. Thay vào đó hãy sử dụng 'flat' **also known as “normalized"**

