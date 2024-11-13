1. **Browser xử lý JS như nào ?**
- Thông qua JS engine, js engine nổi tiếng nhất là V8 của Chrome
Quy trình
1. Tải và phân tích cú pháp (parsing): Khi trình duyệt gặp một file JS, nó sẽ tải và phân tích cú pháp thành "**Abstract Synctax Tree**", một cấu trúc dạng cây biểu diễn các thành phần và cú pháp của mã
2. Biên dịch (Just In Time - JIT): Thay vì chạy trực tiếp, trình duyệt dùng bộ máy JS (engine v8 của Chrome) để biên dịch mã sang dạng máy (machine code) ngay khi cần JIT để tăng tốc độ thực thi
3. Thực thi (Execute): JS là ngôn ngữ đơn luồng (single-threaded), nghĩa là nó thực thi mã từng dòng một trong "Event loop"
- Call Stack: Là nơi gọi hàm và thực thi, khi hoàn thành nó sẽ loại bỏ khỏi ngăn xếp
- Web APIS và Task Squeue: Đối với các tác vụ bất đồng bộ (như `setTimeout, fetch`), trình duyệt sẽ xử lý chúng qua các WebAPI, rồi chuyển kết quả qua hàng đợi tác vụ (Task Queue)
- EventLoop: Liên tục kiểm tra CallStack và TaskQueue. Khi callstack trống, nó sẽ đẩy tác vụ từ TaskQueue vào CallStack
- **Tối ưu hóa**: Các bộ máy JavaScript của trình duyệt sử dụng nhiều kỹ thuật tối ưu hóa, như "Inline Caching" hoặc "Hidden Classes", để tăng hiệu suất cho mã được thực thi thường xuyên.

[Link giải thích](https://www.youtube.com/watch?v=IGkz8Zu9rRk)


2. **Cơ chế hoisting**
Cơ chế đưa các phần khai báo biến và hàm lên các dòng đầu tiên của Scope chứa nó. Tuy nhiên, chỉ di chuyển các phần khai báo, phần gán giá trị vẫn giữ nguyên vị trí cũ.

Là cơ chế cho phép sử dụng biến trước khi dc khai báo, đơn giản vì **parser** thu thập biến, hàm trước khi đọc code nên mới có cơ chế hoisting.

```js
console.log(x); // undefined
var x = 5;
```

```js
sayHello(); // "Hello"

function sayHello() {
    console.log("Hello");
}
```

**Khai báo với `let` và `const`**:
- Các biến khai báo với `let` và `const` cũng bị hoisted, nhưng chúng sẽ không được khởi tạo ngay lập tức và không thể sử dụng trước khi khai báo.
- Khi dùng `let` hoặc `const` trước khi khai báo, JavaScript sẽ gây ra lỗi do chúng đang ở **temporal dead zone** (vùng tạm thời chưa thể sử dụng).

```js
console.log(y); // Lỗi: Cannot access 'y' before initialization
let y = 10;
```

### Tóm tắt
- Với `var`, hoisting sẽ đưa khai báo biến lên đầu và gán giá trị `undefined`.
- Với hàm khai báo, toàn bộ hàm sẽ được hoisted lên đầu phạm vi.
- Với `let` và `const`, hoisting cũng diễn ra nhưng biến chỉ có thể được sử dụng sau khi khai báo.

3. **Callback function là gì?**

**=> Callback function là một function A được truyền vào một function B dưới dạng một tham số. Tại một thời điểm nào đó tùy thuộc vào cách function B được xây dựng mà function A sẽ được function B gọi để thực thi.**

```js
const sayHello = (name, callback) => {
 const msg = "Hello, " + name;
 return callback(msg);
};

const useCallBack = sayHello("Khoa", (msg) => {
 return msg;
});

console.log(useCallBack);
```

vd2:
```js
function fetchData(callback) {
    console.log("Fetching data...");
    setTimeout(() => {
        console.log("Data fetched!");
        callback(); // Gọi callback khi hoàn thành
    }, 2000); // Giả sử việc này mất 2 giây
}

function processData() {
    console.log("Processing data...");
}

fetchData(processData);
```

Khi thực hiện chạy fetchData, sẽ chạy log ra trước, sau đó tới hàm setTImeout, việc fetch sẽ mất 2s và sai khi hoàn thành sẽ gọi hàm callback ra 

Kết quả sẽ là 
```kotlin
Fetching data... 
Data fetched! 
Processing data...
```

3. **closure**
**Closure** trong JavaScript là một tính năng đặc biệt cho phép một function “ghi nhớ” phạm vi (scope) mà nó tạo ra, ngay cả khi hàm đã được thực thi

Có nghĩa là hàm có thể truy cập vào các biến của chính nó 

```js
function createCounter() {
    let count = 0; // Biến này sẽ được "nhớ" bởi hàm bên trong

    return function() {
        count++;
        console.log(count);
    };
}

const counter = createCounter();
counter(); // 1
counter(); // 2
counter(); // 3
```

```js
const increase = () => {
 let x = 0;
 const increaseInner = () => ++x;
 return increaseInner;
};

console.log(increase(); // output: 1
console.log(increase(); // output still: 1

const useClosure = increase();
console.log(useClosure()); // output: 1
console.log(useClosure()); // output: 2 (voila !?)
```

4. Có mấy cách khai báo function
Có 2 cách khai báo
Decalration Function:
```js 
function functionA () {
//logic here
}
```
Expression Function:
```js
const eFuntion = function () {
//logic here
}
```

Declare function sẽ bị ảnh hưởng bởi cơ chế hoisting, còn Expression function thì không. Vì vậy, nếu gọi hàm expression funtion trước khi khai bao thì sẽ bị lỗi

5. **Event Loop**
Cơ chế bất đồng bộ là quá trình mà các câu lệnh chạy cùng một lúc mà không cần chờ câu lệnh trước
Việc xử lý được chia thành các thành phần sau:
- CallStack: Chứa các lệnh được thực thi, khi lệnh chạy sẽ vào ngăn xếp và thực thi xong sẽ được xóa khỏi
- WEB APIS: giữ các lệnh yêu cầu chờ cho tới hết thời gian chờ
- CallBackQueue: Chứa kết quả trả về của WEBAPIS
- Event loop: có nhiệm vụ giám sát tình trạng của CallStack và callbackqueue, khi callstack đã thực thi xong toàn bộ các lệnh của chương trình thì sẽ đẩy callback queue sang callstack

6. **Sử dụng gì để call API ngoài axios**
- AJAX (query)
- fetch (ES6)

7. **Cho câu sau, thứ tự in ra đúng là gì ?**
setTimeout(() => console.log(‘a’),200)
setTimeout(() => console.log(‘b’),0)
console.log(‘c’)

=> Explain: hàm setTimeout là hàm bất đồng bộ, sau khi đọc đến đây. JS Engine sẽ tạm thời đưa vào callback queue để chờ sau khi lệnh console.log(“c”) chạy xong, setTimeout nào có thời gian chờ ngắn hơn, sẽ được xếp trước vào callback queue. Vì vậy, kết quả lần lượt là: 
c
b
a

8. **Khác nhau giữa let,var và const**
var bị ảnh hưởng bởi cơ chế hoisting và hoạt động ở mọi nơi trong global scope
let không bị ảnh hưởng bởi hoisting, có thể tái gán giá trị và hoạt động trong block scope.
const không bị ảnh hưởng bởi hoisting, không thể tái gán giá trị và hoạt động trong block scope.

**Có thể thay đổi giá trị của biến const hay không**
- Const là tham trị: Không thể thay đổi giá trị
- Const là tham chiếu (array, object): được vì bản chất không phải là thay đổi giá trị mà chỉ là thay đổi bộ nhớ


9. **Arrow function và normal function**
Arrow function không làm thay đổi ngữ cảnh của con trỏ **this** và không thể sử dụng agruments.

arguments là object giống Array khả truy cập bên trong hàm, chứa các giá trị của đối số truyền vào trong hàm đó. ... Ghi chú: “Giống Array” tức là arguments có thuộc tính length và đánh chỉ mục từ không (0), nhưng nó không có phương thức dựng sẵn của Array như forEach() và map()

VD về this trong 2 loại function
```js
// Normal function
const obj = {
    name: "Alice",
    sayHello: function() {
        console.log("Hello, " + this.name);
    }
};
obj.sayHello(); // Output: "Hello, Alice"

// Arrow function
const objArrow = {
    name: "Alice",
    sayHello: () => {
        console.log("Hello, " + this.name);
    }
};
objArrow.sayHello(); // Output: "Hello, undefined"
```

Vd về arguments:
```js
// Normal function
function normalFunc() {
    console.log(arguments);
}
normalFunc(1, 2, 3); // Output: [1, 2, 3]

// Arrow function
const arrowFunc = (...args) => {
    console.log(args);
};
arrowFunc(1, 2, 3); // Output: [1, 2, 3]
```

10. **ES6 offer tính năng gì**
Arrow function, class, promise, let & const, template string, destructuring

**Promise**
- Là cách xử lý bất đồng bộ, giúp xử lý các thao tác cần thời gian chờ (gọi API, tải tài nguyên, thực hiện tính toán phức tạp)
- Trạng thái của Promise:
	- Pending (Đang chờ): Khi tác vụ chưa hoàn thành
	- Fulfilled (Đã hoàn thành): Khi tác vụ đã thành công
	- Rejected (Từ chối): Khi có lỗi xảy ra trong quá trình thực hiện

VD Promise
```js
const myPromise = new Promise((resolve, reject) => {
    // giả lập một tác vụ bất đồng bộ như gọi API
    setTimeout(() => {
        const success = true; // giả lập điều kiện thành công

        if (success) {
            resolve("Tác vụ thành công!");
        } else {
            reject("Có lỗi xảy ra!");
        }
    }, 1000);
});
```

Ngoài ra có thể đi kèm với các hàm `.then, .cath, .finnaly`

```js
myPromise
    .then(result => {
        console.log(result); // "Tác vụ thành công!"
    })
    .catch(error => {
        console.error(error); // "Có lỗi xảy ra!"
    })
    .finally(() => {
        console.log("Kết thúc tác vụ.");
    });
```

Sử dụng Promise với nhiều tác vụ bất đồng bộ
```js
const promise1 = Promise.resolve("Hoàn thành 1");
const promise2 = new Promise((resolve) => setTimeout(resolve, 1000, "Hoàn thành 2"));
const promise3 = Promise.resolve("Hoàn thành 3");

Promise.all([promise1, promise2, promise3])
    .then(results => console.log(results)) // ["Hoàn thành 1", "Hoàn thành 2", "Hoàn thành 3"]
    .catch(error => console.error(error));
```

**Template string**
Giúp nhúng biểu thức, các biến trực tiếp vào chuỗi bằng dấu backticks <p>`</p>
vd:
```js
const name = "Alice";
const age = 25;

const greeting = `Hello, my name is ${name} and I am ${age} years old.`;
console.log(greeting); // Output: "Hello, my name is Alice and I am 25 years old."
```

Chuỗi nhiều dòng
```js
const multiLineString = `
    Đây là một chuỗi nhiều dòng.
    Dòng này sẽ nằm trên một dòng mới.
    Dễ đọc và dễ hiểu hơn!
`;
console.log(multiLineString);
```
Bằng cách này, không cần phải sử dụng `/n` hoặc nối chuỗi bằng `+`

**Destructuring**
- Bóc tách phần tử của object (biến tham chiếu)
```js
const numbers = [1, 2, 3, 4];
const [a, b, c] = numbers;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
```

11. **HighOrder Function**
- Là hàm được dùng để nhận nhiều hàm khác làm tham số

```js
function greet(name, callback) {
    console.log(`Hello, ${name}!`);
    callback();
}

function sayGoodbye() {
    console.log("Goodbye!");
}

greet("Alice", sayGoodbye);
// Hello, Alice!
// Goodbye!
```

12. **Kể tên các higher order function trong ES6**
=> reduce, map, filter, foreach
**Foreach****:
-là phương thức thực thi một hàm 1 lần cho mỗi phần tử .nếu mảng có 7 phần tử thì thực thi hàm đó 7 lần. -hàm nhận tham số đầu vào là từng phần tử của mảng và vị trí. forEach( ( item, index ) => {} ) -forEach duyệt tự động theo chiều dài của mảng và mỗi lần duyệt nó sẽ trả về 1 đối tượng . Nói nôm na nó cũng giống như filter() nhưng khác ở chỗ filter() chúng ta cần hứng 1 giá trị gì đó. -filter() thì trả về mảng mới ,còn forEach() không trả về gì cả.

**reduce**
```js
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((accumulator, currentValue) => {
    return accumulator + currentValue;
}, 0);

console.log(sum); // Output: 15
```
Hàm dùng để giảm tham số khi sử dụng logic để đưa ra một kết quả
**map**
- một phương thức trong JavaScript được sử dụng để tạo một mảng mới từ một mảng ban đầu, với mỗi phần tử trong mảng mới là kết quả của việc gọi một hàm callback trên mỗi phần tử của mảng ban đầu.

Phương thức `map` không thay đổi mảng gốc mà trả về một mảng mới với các giá trị đã được xử lý qua hàm callback.

```js
const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = numbers.map(num => num * 2);
console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]
```

**filter**
- Hàm dùng để lọc điều kiện và chỉ lấy các phần tử thỏa điều kiện 
- return: New Array
```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4, 6, 8, 10]
```

13. **Spread operator được dùng khi nào**

- Spread operator được dùng khi muốn clone, merge array/object (Immutable Object)

Let listA  =[a,b,c];
Use Spread operator :  […listA,d,e,f]; (khi clone )

14. Tính chất OOP:

đóng gói, kế thừa, trừu tượng, đa hình
Đóng gói: Ẩn dữ liệu, và truy cập thông qua get, set
```js
class Car { constructor() { 
this._speed = 0; // Ẩn thuộc tính tốc độ 
} 
accelerate() { this._speed += 10; } getSpeed() { return this._speed; } }
```

Trừu tượng:
Ẩn chi tiết thực thi và chỉ cung cấp giao diện

```js
class Animal { makeSound() { 
	throw "This method should be overridden!"; 
} }

class Dog extends Animal { 
makeSound()
{ console.log("Bark"); } 
}
```

Kế thừa
```js
class Animal {
  speak() {
    console.log("Animal makes a sound");
  }
}

class Dog extends Animal {
  speak() {
    console.log("Dog barks");
  }
}
```


Đa hình
Cho phép các đối tượng khác nhau phản hồi lại cùng một fucntion theo cách khác nhau
```js
class Dog {
  speak() {
    console.log("Woof");
  }
}

class Cat {
  speak() {
    console.log("Meow");
  }
}

let dog = new Dog();
let cat = new Cat();

dog.speak();  // "Woof"
cat.speak();  // "Meow"
```

