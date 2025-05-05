

## JavaScript Conditions and Operators

### 1. Comparison Operators

Used to compare two values. Result is `true` or `false`.

| Operator | Description           | Example             |
| -------- | --------------------- | ------------------- |
| `==`     | Equal (loose)         | `5 == "5"` → true   |
| `===`    | Equal (strict)        | `5 === "5"` → false |
| `!=`     | Not equal (loose)     | `5 != "5"` → false  |
| `!==`    | Not equal (strict)    | `5 !== "5"` → true  |
| `>`      | Greater than          | `6 > 3` → true      |
| `<`      | Less than             | `3 < 6` → true      |
| `>=`     | Greater than or equal | `6 >= 6` → true     |
| `<=`     | Less than or equal    | `4 <= 5` → true     |

---

### 2. `==` vs `===`

* `==`: Compares **values**, performs type coercion.
* `===`: Compares **values and types** (recommended).

```javascript
5 == "5";   // true
5 === "5";  // false
```

---

### 3. Logical Operators

Used to combine multiple conditions.

| Operator | Description    | Example               |    |        |   |                |
| -------- | -------------- | --------------------- | -- | ------ | - | -------------- |
| `&&`     | AND            | `true && true` → true |    |        |   |                |
| \`       |                | \`                    | OR | \`true |   | false\` → true |
| `!`      | NOT (negation) | `!true` → false       |    |        |   |                |

---

### 4. Escape Characters

Used inside strings to escape special characters.

| Escape | Meaning      |
| ------ | ------------ |
| `\'`   | Single quote |
| `\"`   | Double quote |
| `\\`   | Backslash    |
| `\n`   | New line     |
| `\t`   | Tab          |

Example:

```javascript
let msg = "He said: \"Hello\"";
```

---

### 5. `typeof` Operator

Returns the **type** of a value.

```javascript
typeof "hello"; // string
typeof 5;       // number
typeof true;    // boolean
typeof {};      // object
typeof undefined; // undefined
```

---

### 6. Branching (Conditions)

Making decisions based on conditions.

#### if

```javascript
if (x > 5) {
  console.log("x is greater than 5");
}
```

#### if / else

```javascript
if (x > 5) {
  console.log("x is big");
} else {
  console.log("x is small");
}
```

#### if / else if / else

```javascript
if (x > 10) {
  console.log("x > 10");
} else if (x > 5) {
  console.log("x > 5");
} else {
  console.log("x <= 5");
}
```

---

### 7. `switch` Statement

Used to check a value against multiple cases.

```javascript
let color = "blue";
switch (color) {
  case "red":
    console.log("Color is red");
    break;
  case "blue":
    console.log("Color is blue");
    break;
  default:
    console.log("Unknown color");
}
```

#### break

Used to **exit** a switch or loop.

---

### 8. Ternary Operator

Short form for if/else.

```javascript
let age = 18;
let result = age >= 18 ? "Adult" : "Minor";
```

#### Multiple statements

```javascript
age >= 18 
  ? (console.log("Adult"), console.log("Allowed")) 
  : console.log("Not allowed");
```

---

### 9. Nesting

Putting conditions inside others.

```javascript
if (x > 0) {
  if (x < 10) {
    console.log("x is between 1 and 9");
  }
}
```

---

### المقارنات والمنطق في JavaScript

* `==` يقارن القيم بعد تحويل النوع تلقائيًا.
* `===` يقارن القيم والنوع معًا (أكثر دقة).
* العوامل المنطقية:

  * `&&` تعني "و".
  * `||` تعني "أو".
  * `!` تعني "نفي".

---

### أحرف الهروب (Escape Characters)

* تُستخدم داخل النصوص لطباعة رموز خاصة مثل سطر جديد أو علامات اقتباس.

---

### typeof

* تُستخدم لمعرفة نوع المتغير (رقم، نص، منطق...).

---

### التحكم في التدفق (الشرط)

* if: ينفذ كود إذا كان الشرط صحيحًا.
* if/else: حالتان حسب تحقق الشرط.
* if/else if/else: أكثر من حالة.
* switch: بديل أنظف لـ if في الحالات المتعددة.
* break: توقف التنفيذ داخل switch أو حلقة.

---

### العامل الثلاثي (Ternary)

* طريقة مختصرة لكتابة if/else في سطر واحد.

---

### التعشيش (Nesting)

* يعني وجود شرط داخل شرط آخر.


