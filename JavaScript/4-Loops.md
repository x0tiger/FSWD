

## JavaScript Loops – Detailed Explanation

### What are Loops?

**Explanation:**
Loops are a programming structure that allows you to execute a block of code repeatedly based on a specific condition. It helps reduce redundancy in code by automating repetitive tasks.

**Arabic Summary:**
الحلقات بتخليك تكرر الكود تلقائيًا بدل ما تكتبه كل مرة.

---

### Types of Loops in JavaScript

There are **3 main types** of loops in JavaScript:

#### 1. `for` loop

**Explanation:**
A `for` loop is used when you **know the exact number of iterations** you want to perform. It is best suited for scenarios where you have a fixed count of repetitions.

**Syntax:**

```javascript
for (initialization; condition; update) {
  // code to be executed
}
```

**Detailed Breakdown:**

* **Initialization:** Used to set up the loop counter (e.g., `let i = 0`).
* **Condition:** The loop continues to run as long as this condition is true (e.g., `i < 5`).
* **Update:** Specifies how the loop counter should change (e.g., `i++`).

**Example:**

```javascript
for (let i = 1; i <= 5; i++) {
  console.log("Number: " + i);
}
```

**Arabic Summary:**
الحلقة دي بنستخدمها لما نكون عارفين عدد التكرارات بالظبط.

---

#### 2. `while` loop

**Explanation:**
A `while` loop continues to execute a block of code as long as a given condition is **true**. It's used when the number of iterations is **not known in advance**.

**Syntax:**

```javascript
while (condition) {
  // code to be executed
}
```

**Example:**

```javascript
let i = 1;
while (i <= 5) {
  console.log("Number: " + i);
  i++;
}
```

**Arabic Summary:**
الحلقة دي بنستخدمها لما نكون مش عارفين عدد التكرارات، ولكن عارفين الشرط.

---

#### 3. `do...while` loop

**Explanation:**
The `do...while` loop is similar to the `while` loop, but the main difference is that the code will **always run at least once**, even if the condition is false.

**Syntax:**

```javascript
do {
  // code to be executed
} while (condition);
```

**Example:**

```javascript
let i = 6;
do {
  console.log("Number: " + i);
  i++;
} while (i <= 5);
```

**Arabic Summary:**
الحلقة دي بتننفذ الكود مرة واحدة على الأقل حتى لو الشرط غير صحيح.

---

### What is an Iterator?

**Explanation:**
An iterator is the variable used to keep track of the current position in a loop. It often represents a counter that changes with each loop iteration.

**Example:**

```javascript
for (let i = 0; i < 3; i++) {
  console.log("i is now: " + i);
}
```

**Arabic Summary:**
الـ Iterator هو المتغير اللي بنزوده أو ننقصه مع كل لفة في الحلقة.

---

### What is an Infinite Loop?

**Explanation:**
An infinite loop is a loop that never stops because its exit condition is never satisfied, meaning it keeps running forever.

**Example:**

```javascript
while (true) {
  console.log("This will run forever!");
}
```

**Arabic Summary:**
الحلقة اللانهائية هي حلقة بتستمر للأبد لأن الشرط مش بيتحقق أبدًا.

---

### Using Logical Operators with Loops

**Explanation:**
Logical operators like `&&` (AND) and `||` (OR) can be used inside the loop condition to combine multiple conditions.

**Example:**

```javascript
let i = 1;
while (i <= 10 && i !== 7) {
  console.log(i);
  i++;
}
```

**Arabic Summary:**
بنستخدم "&&" و "||" لتحديد أكتر من شرط للحلقة.

---

### What is `break`?

**Explanation:**
The `break` keyword is used to **exit a loop** immediately, even if the loop's condition is still true. It stops further iterations.

**Example:**

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;
  }
  console.log(i); // Prints numbers 0 to 4
}
```

**Arabic Summary:**
`break` بيوقف الحلقة فورًا لما يتحقق شرط معين.

---

### What is `continue`?

**Explanation:**
The `continue` keyword is used to **skip the current iteration** and move on to the next iteration of the loop.

**Example:**

```javascript
for (let i = 1; i <= 5; i++) {
  if (i === 3) {
    continue;
  }
  console.log(i); // Skips 3 and prints 1, 2, 4, 5
}
```

**Arabic Summary:**
`continue` بيتخطى التكرار الحالي ويمشي على التكرار اللي بعده.


