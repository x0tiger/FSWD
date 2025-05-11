

## JavaScript Loops – Detailed Explanation

### What are loops?

Loops are used to execute a block of code repeatedly as long as a specific condition is true.

**الاختصار بالعربي:**
الحلقات بتخلينا نكرر كود معين بدل ما نكتبه أكتر من مرة.

---

### Types of Loops in JavaScript

#### 1. `for` loop

Used when the number of repetitions is known in advance.

**Structure:**

```javascript
for (initialization; condition; update) {
  // code block to execute
}
```

**Example:**

```javascript
for (let i = 1; i <= 5; i++) {
  console.log("Number: " + i);
}
```

**الاختصار بالعربي:**
بنستخدمها لما نكون عارفين هنكرر الكود كام مرة بالظبط.

---

#### 2. `while` loop

Runs a block of code as long as a condition is true.

**Example:**

```javascript
let i = 1;
while (i <= 5) {
  console.log("Number: " + i);
  i++;
}
```

**الاختصار بالعربي:**
بنستخدمها لما مش عارفين العدد بالظبط، بس عارفين شرط التوقف.

---

#### 3. `do...while` loop

Like `while`, but the code runs at least once even if the condition is false.

**Example:**

```javascript
let i = 6;
do {
  console.log("Number: " + i);
  i++;
} while (i <= 5);
```

**الاختصار بالعربي:**
بتنفذ الكود مرة واحدة على الأقل حتى لو الشرط غلط من البداية.

---

### What is an Iterator?

An iterator is a variable that changes with each loop repetition.

**Example:**

```javascript
for (let i = 0; i < 3; i++) {
  console.log("i is now: " + i);
}
```

**الاختصار بالعربي:**
هو المتغير اللي بنزوده أو ننقصه مع كل لفة.

---

### What is an Infinite Loop?

A loop that never stops because the condition never becomes false.

**Example:**

```javascript
while (true) {
  console.log("This will run forever!");
}
```

**الاختصار بالعربي:**
حلقة مش بتنتهي لأن شرط التوقف عمره ما بيتحقق.

---

### Using Logical Operators with Loops

Logical operators like `&&` (AND) or `||` (OR) can be used in loop conditions.

**Example:**

```javascript
let i = 1;
while (i <= 10 && i !== 7) {
  console.log(i);
  i++;
}
```

**الاختصار بالعربي:**
بنستخدم "&&" و "||" عشان نحط أكتر من شرط للحلقة.

---

### What is `break`?

`break` stops the loop immediately when a certain condition is met.

**Example:**

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;
  }
  console.log(i);
}
```

**الاختصار بالعربي:**
بيوقف الحلقة خالص أول ما الشرط يتحقق.

---

### What is `continue`?

`continue` skips the current iteration and moves to the next one.

**Example:**

```javascript
for (let i = 1; i <= 5; i++) {
  if (i === 3) {
    continue;
  }
  console.log(i);
}
```

**الاختصار بالعربي:**
بيعدي السطر ويدخل على اللفة اللي بعدها لو الشرط اتحقق.

