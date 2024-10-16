Tags: #react #js 
Reference: [Sự khác nhau Shallow Copy và Deep Copy](https://viblo.asia/p/su-khac-nhau-giua-deep-copy-va-shallow-copy-trong-javascript-4dbZN3qylYM)
# Các kiểu dữ liệu nguyên thủy
- Number
- String
- Boolean
- undefined
- null
Với kiểu dữ liệu nguyên thủy, khi được gán giá trị sẽ được gắn chặt với biến
=>> Không cần lo lắng về việc copy các biến này vì sẽ luôn có một bản sao (tách biệt hoàn toàn so với biến cũ)

# Kiểu dữ liệu hỗn hợp (Object và Array)
- Về bản chất, array cũng là một object
```js
let a = []
type of a // 'object'
```

Nhưng khi copy object hoặc array vào biến mới, biến đó sẽ chỉ tham chiếu của giá trị ban đầu
```js
const a = {
  en: 'Hello',
  vi: 'Xin chào'
}

let b = a
b.vi = 'Chao xìn'
console.log(b.vi) // Chao xìn
console.log(a.vi) // Chao xìn
```
# Object 
## Spread operator
- Spread operator là **toán tử 3 chấm**

```js
const a = {
  en: 'Hello',
  vi: 'Xin chào'
}

let b = {...a}
b.vi = 'Chao xìn'
console.log(b.vi) // Chao xìn
console.log(a.vi) // Xin chào
```
Kết hợp nhiều array
`const d = {...a, ...b, ...c}`

## Object.assign
- Cách dùng phổ biến trước khi Spread operator được phát minh, cũng ra kết quả tương tự. 
- Lưu ý, các thành phần đối số thử 2 tở đi, bạn có thể assign object cần copy với một object rỗng {}
```js
const a = {
  en: 'Hello',
  vi: 'Xin chào'
}

let b = Object.assign({}, a)
b.vi = 'Chao xìn'
console.log(b.vi) // Chao xìn
console.log(a.vi) // Xin chào
```

## Cạm bẫy: Object lồng nhau
```js
const a = {
  languages: {
    vi: 'Xin chào'
  }
}
let b = {...a}
b.languages.vi = 'Chao xìn'
console.log(b.languages.vi) // Chao xìn
console.log(a.languages.vi) // Chao xìn
```
Để giải quyết vấn đề này, stringify object sau đó parse nó

```js
const a = {
  languages: {
    vi: 'Xin chào'
  }
}
let b = JSON.parse(JSON.stringify(a))
b.languages.vi = 'Chao xìn'
console.log(b.languages.vi) // Chao xìn
console.log(a.languages.vi) // Xin chào
```

Điều này cũng được áp dụng tương tự với Array

