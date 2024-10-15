Tags: #js #es6
### . **`forEach()`**

- Phương thức này được sử dụng để duyệt qua các phần tử của mảng và thực thi một hàm với từng phần tử đó.
```js
const arr = [1, 2, 3]; arr.forEach((item) => console.log(item)); // 1, 2, 3
```
### 2. **`map()`**
- Phương thức này tạo ra một mảng mới với kết quả của việc gọi hàm truyền vào cho mỗi phần tử trong mảng.

```js
const arr = [1, 2, 3]; 
const squared = arr.map(num => num * 2); 
console.log(squared); // [2, 4, 6]`
```

### 3. **`filter()`**
- Phương thức này tạo ra một mảng mới với các phần tử thỏa mãn điều kiện của hàm được truyền vào.

```js
const arr = [1, 2, 3, 4]; 
const evens = arr.filter(num => num % 2 === 0); 
console.log(evens); // [2, 4]
```

### 4. **`reduce()`**

- Phương thức này giúp thực hiện một phép tính lặp trên mảng, trả về một giá trị duy nhất dựa trên các phần tử của mảng.

```js
const arr = [1, 2, 3, 4]; 
const sum = arr.reduce((acc, num) => acc + num, 0); 
console.log(sum); // 10
```

### 5. **`find()`**

- Phương thức này trả về **phần tử đầu tiên** trong mảng thỏa mãn điều kiện của hàm được truyền vào. Nếu không tìm thấy, nó sẽ trả về `undefined`.

```js
const arr = [1, 2, 3, 4]; const found = arr.find(num => num > 2); console.log(found); // 3
```

### 6. **`findIndex()`**

- Phương thức này trả về **chỉ số của phần tử đầu tiên** trong mảng thỏa mãn điều kiện của hàm. Nếu không tìm thấy, nó trả về `-1`.

```js
const arr = [1, 2, 3, 4]; 
const index = arr.findIndex(num => num > 2); 
console.log(index); // 2
```

### 7. **`some()`**

- Phương thức này kiểm tra xem có **ít nhất một phần tử** trong mảng thỏa mãn điều kiện của hàm không. Nó trả về `true` nếu có và `false` nếu không.

```js
const arr = [1, 2, 3]; 
const hasEven = arr.some(num => num % 2 === 0); 
console.log(hasEven); // true
```

### 8. **`every()`**

- Phương thức này kiểm tra xem **tất cả các phần tử** trong mảng có thỏa mãn điều kiện của hàm không. Nó trả về `true` nếu đúng và `false` nếu sai.

```js
const arr = [2, 4, 6]; 
const allEven = arr.every(num => num % 2 === 0); 
console.log(allEven); // true
```

### 9. **`includes()`**

- Phương thức này kiểm tra xem mảng có **chứa một giá trị cụ thể** nào đó hay không. Nó trả về `true` nếu có và `false` nếu không.

```js
const arr = [1, 2, 3]; console.log(arr.includes(2)); // true console.log(arr.includes(5)); // false
```

### 10. **`from()`**

- Phương thức này tạo ra một mảng mới từ một đối tượng dạng mảng hoặc một đối tượng có thể lặp lại.

```js
const str = "hello"; 
const arr = Array.from(str); 
// ['h', 'e', 'l', 'l', 'o']
```

### 11. **`of()`**

- Phương thức này tạo ra một mảng mới với các phần tử truyền vào (khác với cách khởi tạo mảng thông thường khi truyền vào một số sẽ tạo mảng có độ dài tương ứng).

```js
const arr = Array.of(7, 2, 3); 
console.log(arr); // [7, 2, 3]
```

### 12. **`fill()`**

- Phương thức này điền một giá trị cụ thể vào tất cả các phần tử trong mảng từ chỉ số bắt đầu đến chỉ số kết thúc.
- Điền 1 giá trị a vapf tất cả các phần tử có chỉ số từ start -> end

```js
const arr = [1, 2, 3, 4]; 
arr.fill(0, 1, 3);
// [1, 0, 0, 4]
```

### 13. **`entries()`, `keys()`, `values()`**

- `entries()`: Trả về một iterator chứa cả chỉ số và giá trị của mảng.
- `keys()`: Trả về một iterator chỉ chứa các chỉ số của mảng.
- `values()`: Trả về một iterator chỉ chứa các giá trị của mảng.

```js
const arr = ['a', 'b', 'c']; 
for (let [index, value] of arr.entries()) {  
	console.log(index, value); // 0 'a', 1 'b', 2 'c' 
}
```

### 14. `IndexOf()`

The indexOf() method returns the first index at which a given element can be found in the array, or -1 if it is not present.

![coding indexOf](https://a.storyblok.com/f/152334/1406x792/13698e2956/indexof.png)