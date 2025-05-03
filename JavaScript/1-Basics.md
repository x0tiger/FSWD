

# JavaScript Basics

## What is JavaScript?

JavaScript is a high-level, interpreted programming language used to add interactivity, logic, and dynamic behavior to webpages. It runs in the browser and allows developers to manipulate the DOM, handle events, and communicate with servers.

---

## Syntax vs. Semantics

- **Syntax**: The structure or format of the code (rules about how JavaScript statements should be written).
- **Semantics**: The meaning or behavior of the code (what the code is supposed to do).

Example:
```javascript
let name = "Ali"; // Correct syntax and meaningful
let = name "Ali"; // Wrong syntax
````

---

## Blocks, Statements, and Keywords

* **Block**: A group of code enclosed in `{}`.
* **Statement**: A single instruction like a variable declaration or loop.
* **Keyword**: Reserved words in JavaScript like `let`, `const`, `if`, `function`.

---

## What is a Semicolon? Is it optional?

* A semicolon `;` ends a statement.
* JavaScript can insert semicolons automatically in some cases (ASI: Automatic Semicolon Insertion), but it's best practice to write them manually.

---

## How to Include JavaScript in HTML?

1. **Inline**:

```html
<button onclick="alert('Hello')">Click Me</button>
```

2. **Internal**:

```html
<script>
  alert("Hello from script!");
</script>
```

3. **External**:

```html
<script src="main.js"></script>
```

---

## Values, Literals, and Variables

* **Value**: Data like `"Hello"`, `42`, `true`.
* **Literal**: Fixed value written in the code like `"Ahmed"` or `10`.
* **Variable**: A named container that stores a value.

---

## Data Types: Numbers, Strings, and Booleans

* **Number**: `1`, `5.7`, `-10`
* **String**: `"text"`, `'hello'`
* **Boolean**: `true`, `false`

---

## Declaring Variables in JavaScript

You can declare using:

```javascript
var x = 10;
let y = 20;
const PI = 3.14;
```

* `var`: function-scoped
* `let`: block-scoped (preferred)
* `const`: block-scoped and constant (cannot be reassigned)

---

## Variable Naming Rules

* Must start with a letter, `$`, or `_`
* Can include digits but not at the beginning
* Case-sensitive
* Cannot use reserved keywords (`if`, `let`, `return`)

---

## Dynamic Typing in JavaScript

JavaScript is **dynamically typed**, meaning the variable type is determined at runtime.

Example:

```javascript
let data = 42;       // data is a number
data = "text";       // now it's a string
```

---

## Undefined vs. Null

* **undefined**: Automatically assigned to variables that are declared but not assigned a value.
* **null**: Intentionally assigned to indicate "no value".

### Example:

```javascript
let a;
console.log(a); // undefined

let b = null;
console.log(b); // null
```

* `undefined` means "not yet set"
* `null` means "intentionally empty"

---

## Summary in Arabic (اختصار):

* **JavaScript** هي لغة برمجة تعمل في المتصفح وتتحكم في محتوى وصفحات الويب.
* **Syntax** معناها "شكل الكود"، و**Semantics** معناها "معنى الكود".
* **Block** هو مجموعة أوامر بين `{}`.
* **Semicolon** مهم لكنه أحيانًا اختياري.
* ممكن نكتب JavaScript داخل صفحة HTML بثلاث طرق: Inline, Internal, External.
* JavaScript تدعم أنواع بيانات زي: الأرقام، النصوص، والقيم المنطقية.
* المتغيرات ممكن تتغير أنواعها لأن JavaScript **ديناميكية**.
* **undefined** معناها "لسه متحددش"، و**null** معناها "فاضي متعمدًا".

```

```
