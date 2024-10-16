Tags: #js #react 
Reference: [JS Array Methods](https://www.w3schools.com/js/js_array_methods.asp)
Version ES6
# Basic Array Methods
1. [[#JavaScript Array length]]
2. [[#JavaScript Array toString()]]
3. [[#JavaScript Array at()]]
4. [[#JavaScript Array join()]]
5. [[#JavaScript Array pop()]]
6. [[#JavaScript Array push()]]
7. [[#JavaScript Array shift()]]
8. [[#JavaScript Array unshift()]]
9. [[#JavaScript Array delete()]]
11. Array flat()
12. Array splice()
13. Array toSpliced()
14. Array slice()

## JavaScript Array length

The `length` property returns the length (size) of an array:

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
let size = fruits.length; //4
```

## JavaScript Array toString()

The JavaScript method `toString()` converts an array to a string of (comma separated) array values.

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
document.getElementById("demo").innerHTML = fruits.toString(); 
// Banana,Orange,Apple,Mango
```

## JavaScript Array at()

Get the third element of fruits using at():
```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
let fruit = fruits.at(2); // Apple (0 -> 1 -> 2)
```

Get the third element of fruits using []:
```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
let fruit = fruits[2];
```

## JavaScript Array join()

The `join()` method also joins all array elements into a string.

It behaves just like `toString()`, but in addition you can specify the separator:

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
document.getElementById("demo").innerHTML = fruits.join(" * ");
// Banana * Orange * Apple * Mango
```
## JavaScript Array pop()

The `pop()` method **removes** the last element from an array:

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
fruits.pop();
// const fruits = ["Banana", "Orange", "Apple"]
```

The `pop()` method returns the value that was "popped out":

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
let fruit = fruits.pop();
// fruit = "Mango"
```

## JavaScript Array push()

The `push()` method adds a new element to an array (at the end):

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
fruits.push("Kiwi"); // return new length if print
// fruits = ["Banana", "Orange", "Apple", "Mango", "Kiwi"]; 
```

## JavaScript Array shift()

The `shift()` method removes the first array element and "shifts" all other elements to a lower index.

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
fruits.shift();
// fruits = ["Orange", "Apple", "Mango"]; 
```

The `shift()` method returns the value that was "shifted out":
`fruits.shift(); // return "Orange"`

## JavaScript Array unshift()

The `unshift()` method adds a new element to an array (at the beginning), and "unshifts" older elements: (Hiểu đơn giản là thêm một phần tử vào đầu Array)

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
fruits.unshift("Lemon"); // return new length => 4 -> 5
//"Lemon", "Banana", "Orange", "Apple", "Mango"
```

## Changing element

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
fruits[0] = "Kiwi";
```

### JavaScript Array length
The `length` property provides an easy way to append a new element to an array:
(Thêm vào phần tử cuối)
```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
fruits[fruits.length] = "Kiwi"; 
// Banana,Orange,Apple,Mango,Kiwi
```

## JavaScript Array delete()

<font color="#ff0000"><span style="background:rgba(240, 107, 5, 0.2)"><center>### Warning !</span></font>

<font color="#ff0000"><span style="background:rgba(240, 107, 5, 0.2)"><p>Using `delete()` leaves `undefined` holes in the array.</p></span></font>

<font color="#ff0000"><span style="background:rgba(240, 107, 5, 0.2)"><p>Use pop() or shift() instead.</p></center></span></font>
```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
delete fruits[0]; 
// fruits[0] is undefined
```

## Merging Arrays (Concatenating)

Concatenation means joining strings end-to-end.
Nghĩa là nối chuỗi

## JavaScript Array concat()

The `concat()` method creates a new array by merging (concatenating) existing arrays:
( Nối chuỗi c = a + b )
```js
const myGirls = ["Cecilie", "Lone"];  
const myBoys = ["Emil", "Tobias", "Linus"];  
  
const myChildren = myGirls.concat(myBoys);
// Cecilie,Lone,Emil,Tobias,Linus
```
- The `concat()` method does not change the existing arrays. **It always returns a new array.**
- The `concat()` method can take any number of array arguments.

## JavaScript Array flat()

`flat()` được sử dụng để "làm phẳng" một mảng nhiều chiều thành một mảng một chiều.
Nó tạo ra một bản sao mới của mảng gốc với tất cả các phần tử lồng nhau được đưa lên cấp độ bề mặt dựa trên mức độ làm phẳng mà bạn chỉ định.

`array.flat([depth]);`

```js
const arr = [1, 2, [3, 4]]; const flatArr = arr.flat(); console.log(flatArr); // [1, 2, 3, 4]
```
Làm phẳng nhiều lớp
```js
const arr = [1, 2, [3, 4, [5, 6]]];
const flatArr = arr.flat(2);
console.log(flatArr); // [1, 2, 3, 4, 5, 6]
```

## Javascript Array flatMap()

Trong JavaScript, phương thức `flatMap()` kết hợp cả `map()` và `flat()` thành một bước duy nhất. Đầu tiên, nó sẽ áp dụng hàm `map()` trên từng phần tử của mảng, sau đó làm phẳng kết quả một cấp độ.

```js
const myArr = [1, 2, 3, 4, 5, 6];  
const newArr = myArr.flatMap(x => [x, x * 10]);
// 1,10,2,20,3,30,4,40,5,50,6,60
```
## JavaScript Array splice()

The `splice()` method can be used to add new items to an array:

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
fruits.splice(2, 0, "Lemon", "Kiwi");
// Banana,Orange,Lemon,Kiwi,Apple,Mango
```
- The first parameter (2) defines the position **where** new elements should be **added** (spliced in).
- The second parameter (0) defines **how many** elements should be **removed**.
- The rest of the parameters ("Lemon" , "Kiwi") define the new elements to be **added**.
- The `splice()` method returns an array with the deleted items:
### Using splice to remove element

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];  
fruits.splice(0, 1);
// "Orange", "Apple", "Mango"
```
## JavaScript Array toSpliced()

Phương thức **`toSpliced()`** là một phần của **Array.prototype** được giới thiệu gần đây trong phiên bản ECMAScript 2023 (ES13). Nó rất giống với phương thức **`splice()`**, nhưng **`toSpliced()`** **không thay đổi mảng gốc** mà thay vào đó **trả về một bản sao mới** với những thay đổi đã áp dụng. Điều này giúp làm việc với các mảng một cách an toàn hơn khi bạn cần giữ nguyên mảng ban đầu.

`array.toSpliced(start, deleteCount[, item1[, item2[, ...]]])

- `start`: Vị trí bắt đầu thao tác trong mảng.
- `deleteCount`: Số phần tử cần xóa từ vị trí `start`.
- `item1`, `item2`, ... (tùy chọn): Các phần tử mới được thêm vào tại vị trí `start`.

### Điểm khác biệt chính:

- `splice()`: Thay đổi mảng ban đầu.
- `toSpliced()`: Tạo ra một mảng mới mà không thay đổi mảng ban đầu.

```js
const arr = [1, 2, 3, 4, 5];
const newArr = arr.toSpliced(2, 1); // Xóa 1 phần tử tại vị trí 2
console.log(newArr); // [1, 2, 4, 5]
console.log(arr);    // [1, 2, 3, 4, 5] (mảng gốc không thay đổi)
```

## JavaScript Array slice()

- Phương thức **`slice()`** được sử dụng để sao chép một phần của mảng hoặc chuỗi thành một mảng mới hoặc chuỗi mới mà **không làm thay đổi mảng/chuỗi ban đầu**. 
- Nó trả về một mảng mới chứa các phần tử từ mảng gốc dựa trên chỉ số bắt đầu và kết thúc mà bạn cung cấp.

`array.slice([start[, end]])`

```js
const arr = [1, 2, 3, 4, 5];
const slicedArr = arr.slice(2);
console.log(slicedArr); // [3, 4, 5]
console.log(arr);       // [1, 2, 3, 4, 5] (mảng gốc không thay đổi)
```
 Sử dụng số âm cho props start
 ```js
const arr = [1, 2, 3, 4, 5];
const slicedArr = arr.slice(-2); 
console.log(slicedArr); // [4, 5]
```
## [[Array Function trong ES6]]
