

### ✅ What are functions?

A function is a reusable block of code designed to perform a particular task. Instead of repeating the same code, you can define a function once and call it whenever needed.

**Example:**

```javascript
function greetUser(name) {
  return "Hello, " + name + "!";
}

let message = greetUser("Ahmed");
console.log(message); // Output: Hello, Ahmed!
```

**🔸 بالعربي:**
الدالة هي كود بيعمل مهمة معينة. ممكن تنادي عليها بأي وقت بدل ما تكتب الكود تاني.

---

### ✅ How to create functions in JavaScript?

You can create a function using the `function` keyword, followed by a name, parameters (if any), and the function body.

**Example:**

```javascript
function sayHello() {
  console.log("Hello, world!");
}

sayHello(); // Calls the function
```

**🔸 بالعربي:**
بنستخدم كلمة function وبعدها اسم الدالة والأقواس، وجواهم الكود اللي بيتنفذ.

---

### ✅ Built-in vs. User-defined Functions

* **Built-in**: Provided by JavaScript (e.g. `alert()`, `parseInt()`).
* **User-defined**: Functions you write yourself for custom tasks.

**🔸 بالعربي:**
في دوال جاهزة من جافاسكريبت، ودوال بتكتبها انت علشان مهام معينة.

---

### ✅ Categories of User-defined Functions

1. Function with no parameter & no return.
2. Function with parameter & no return.
3. Function with parameter & return.

**Examples:**

```javascript
function showMessage() {
  console.log("Welcome!");
}

function greet(name) {
  console.log("Hi " + name);
}

function sum(a, b) {
  return a + b;
}
```

**🔸 بالعربي:**
في دوال من غير باراميتر، ودوال بتاخد باراميتر، ودوال بترجع ناتج.

---

### ✅ What is "return" and "arguments"?

* `return`: Sends back a value from the function.
* `arguments`: A built-in object holding all passed parameters.

**Example:**

```javascript
function multiply(a, b) {
  return a * b;
}

let result = multiply(5, 4);
console.log(result); // 20
```

**🔸 بالعربي:**
`return` بترجع نتيجة من الدالة. `arguments` بتشوف بيها الباراميتر اللي دخلت.

---

### ✅ How to call functions?

You call a function using its name followed by parentheses.

```javascript
function welcome() {
  console.log("Hello!");
}

welcome(); // Calling the function
```

**🔸 بالعربي:**
بنادي على الدالة باسمها وكأنها أمر.

---

### ✅ What is NaN in JavaScript?

NaN stands for "Not a Number". It shows up when a value can't be interpreted as a number.

```javascript
let x = "abc" * 3;
console.log(x); // NaN
```

**🔸 بالعربي:**
معناها مش رقم، بتظهر لو حاولت تضرب أو تجمع قيمة مش رقمية.

---

### ✅ What are anonymous functions?

Functions without a name, usually used when passing them as values.

```javascript
let greet = function(name) {
  return "Hi, " + name;
};

console.log(greet("Sara")); // Hi, Sara
```

**🔸 بالعربي:**
دوال بدون اسم، غالبًا بنستخدمها كمتغير.

---

### ✅ What are callback functions?

A function passed as an argument to another function.

```javascript
function processUser(name, callback) {
  callback(name);
}

processUser("Ali", function(n) {
  console.log("Welcome, " + n);
});
```

**🔸 بالعربي:**
دالة بنبعتها كوسيط لدالة تانية علشان تتنفذ جواها.

---

### ✅ What is a Self-Invoked Function?

A function that runs itself immediately after being defined.

```javascript
(function() {
  console.log("This runs immediately");
})();
```

**🔸 بالعربي:**
دالة بتشتغل لوحدها أول ما تتكتب.

---

### ✅ What is IIFE (Immediately Invoked Function Expression)?

It's another name for a self-invoked function. Often used to create a private scope.

```javascript
(function(name) {
  console.log("Hello, " + name);
})("Ziad");
```

**🔸 بالعربي:**
اختصار لنوع دالة بتشتغل فورًا وبتعمل عزل للكود.

---

### ✅ What are closures in JavaScript?

A closure gives you access to an outer function’s scope from an inner function.

```javascript
function outer() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}

let counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
```

**🔸 بالعربي:**
الكلوجر بتخلي الدالة الداخلية تفتكر المتغيرات اللي في الدالة الخارجية.


