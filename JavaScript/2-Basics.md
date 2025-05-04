
## JavaScript Basics 2

### 1. Logging and Output

#### console.log()

تستخدم لطباعة القيم إلى نافذة الكونسول (Console) في المتصفح.

```javascript
console.log("Hello World");
console.log(5 + 3); // 8
```

#### alert() و window\.alert()

تستخدم لعرض رسالة منبثقة للمستخدم.

```javascript
alert("Welcome!");
window.alert("This is also an alert.");
```

#### document.write() و document.writeln()

تكتب مباشرة في صفحة HTML. غير مفضلة حاليًا.

```javascript
document.write("Hello from JavaScript!");
document.writeln("<br>This is a new line");
```

---

### 2. Comments in JavaScript

#### تعليقات سطر واحد

```javascript
// This is a single-line comment
```

#### تعليقات متعددة الأسطر

```javascript
/*
  This is a multi-line comment.
  Used to explain code in more detail.
*/
```

---

### 3. Operators in JavaScript

#### أنواع العمليات

* Arithmetic Operators (عمليات حسابية)
* Assignment Operators (إسناد)
* Comparison Operators (مقارنة)
* Logical Operators (منطقية)
* String Operators (ربط نصوص)
* Type Operators (أنواع البيانات)
* Bitwise Operators (بتات)
* Ternary Operator (شرط مختصر)

---

### 4. Arithmetic Operators

| Operator | Description         | Example    | Result |
| -------- | ------------------- | ---------- | ------ |
| +        | Addition            | 5 + 3      | 8      |
| -        | Subtraction         | 5 - 3      | 2      |
| \*       | Multiplication      | 5 \* 3     | 15     |
| /        | Division            | 6 / 2      | 3      |
| %        | Modulus (remainder) | 7 % 3      | 1      |
| \*\*     | Exponentiation      | 2 \*\* 3   | 8      |
| ++       | Increment           | x++ or ++x | +1     |
| --       | Decrement           | x-- or --x | -1     |

---

### 5. Precedence and Associativity

* **Precedence**: ترتيب تنفيذ العمليات حسب الأولوية.
* **Associativity**: اتجاه تنفيذ العمليات عند تساوي الأولوية (يمين أو يسار).

مثال:

```javascript
console.log(5 + 2 * 3); // 11 لأن * لها أولوية أعلى من +
```

---

### 6. Assignment Operators

| Operator | Example | Meaning    |
| -------- | ------- | ---------- |
| =        | x = 10  | Assign     |
| +=       | x += 2  | x = x + 2  |
| -=       | x -= 2  | x = x - 2  |
| \*=      | x \*= 3 | x = x \* 3 |
| /=       | x /= 2  | x = x / 2  |
| %=       | x %= 2  | x = x % 2  |

---

### 7. الفرق بين ++x و x++

```javascript
let x = 5;
console.log(x++); // 5 ثم يصبح x = 6
console.log(++x); // 7 لأن ++x تزيد أولاً
```

---

### 8. String Concatenation

```javascript
let first = "Ahmed";
let last = "Hassan";
let full = first + " " + last;
console.log(full); // Ahmed Hassan
```

---

### ملخص بالعربي:

* `console.log` تطبع في الكونسول.
* `alert` تظهر تنبيه للمستخدم.
* `document.write` تطبع على الصفحة مباشرة.
* التعليقات تساعد في توثيق الكود.
* توجد أنواع كثيرة من العمليات في JavaScript.
* يجب فهم ترتيب وأولوية العمليات.
* الفرق بين `++x` و `x++` في توقيت الزيادة.

---

