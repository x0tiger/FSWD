

## Arrays in JavaScript

### What are arrays in JavaScript?

**Explanation:**
An array is a special variable that holds **multiple values** in a single variable name. You can store numbers, strings, objects, or even other arrays.

```javascript
let colors = ["red", "green", "blue"];
```

**Arabic Summary:**
المصفوفة هي متغير بيحتوي على مجموعة قيم بدل ما تعمل متغير لكل قيمة.

---

### How to create an array in JavaScript?

**Syntax:**

```javascript
let fruits = ["apple", "banana", "mango"];
```

You can also use the `Array` constructor:

```javascript
let numbers = new Array(1, 2, 3);
```

**Arabic Summary:**
تقدر تعمل مصفوفة باستخدام \[] أو باستخدام `new Array()`.

---

### How to get and set values from and to arrays?

**Access by index:**

```javascript
let fruits = ["apple", "banana"];
console.log(fruits[0]); // "apple"
```

**Update value:**

```javascript
fruits[1] = "orange";
```

**Arabic Summary:**
بتستخدم الرقم اللي بيمثل ترتيب العنصر (index) علشان توصله أو تعدله.

---

### What is `console.table` function?

**Explanation:**
`console.table()` prints array (or object) data in a tabular format in the console, which is easier to read.

```javascript
let cars = ["BMW", "Toyota", "Ford"];
console.table(cars);
```

**Arabic Summary:**
بتعرض المصفوفة على شكل جدول في الـ Console لسهولة القراءة.

---

### Array methods: `pop`, `push`, `shift`, `unshift`, `splice`, `join`, `concat`

#### `push()` – Add item at end

```javascript
fruits.push("grape");
```

#### `pop()` – Remove last item

```javascript
fruits.pop();
```

#### `unshift()` – Add item at beginning

```javascript
fruits.unshift("lemon");
```

#### `shift()` – Remove first item

```javascript
fruits.shift();
```

#### `splice()` – Add/remove at specific index

```javascript
fruits.splice(1, 1); // remove 1 item at index 1
```

#### `join()` – Convert array to string

```javascript
fruits.join(", ");
```

#### `concat()` – Merge arrays

```javascript
let allFruits = fruits.concat(["kiwi", "pear"]);
```

**Arabic Summary:**

* `push` و `unshift`: لإضافة عناصر
* `pop` و `shift`: لإزالة عناصر
* `splice`: للإضافة أو الحذف بمكان معين
* `join`: لتحويل المصفوفة إلى نص
* `concat`: لدمج مصفوفتين

---

### How to get the length of an array?

```javascript
let length = fruits.length;
```

**Arabic Summary:**
خاصية `length` بتديك عدد العناصر في المصفوفة.

---

## Objects in JavaScript

### What are objects in JavaScript?

**Explanation:**
Objects are collections of properties (key-value pairs). Each property has a name (key) and a value.

```javascript
let person = {
  name: "Ali",
  age: 25,
  job: "developer"
};
```

**Arabic Summary:**
الكائن بيخزن بيانات على هيئة مفتاح وقيمة (key: value).

---

### How to get and set values from and to objects?

**Accessing values:**

```javascript
console.log(person.name);
console.log(person["age"]);
```

**Setting values:**

```javascript
person.age = 30;
person["job"] = "designer";
```

**Arabic Summary:**
تقدر توصل أو تعدل القيم باستخدام `.` أو `[]`.

---

### What is the meaning of array of objects?

**Explanation:**
It’s an array that contains multiple object elements.

```javascript
let users = [
  { name: "Ali", age: 25 },
  { name: "Sara", age: 22 }
];
```

**Arabic Summary:**
مصفوفة تحتوي على كائنات، كل كائن فيه بيانات مختلفة.

---

### How to map an array into another format using loops?

**Using `for` loop:**

```javascript
let names = [];
for (let i = 0; i < users.length; i++) {
  names.push(users[i].name);
}
```

**Using `map()` method:**

```javascript
let names = users.map(user => user.name);
```

**Arabic Summary:**
تقدر تحول المصفوفة لصيغة جديدة باستخدام `for` أو `map`.

