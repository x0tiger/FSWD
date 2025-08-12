
### 1. **What are the different operators in PHP?**

In PHP, operators are symbols you use to perform operations like:

* Assigning values
* Doing math
* Comparing values
* Working with strings
* Making logic decisions

Main types:

* Assignment operators
* Arithmetic operators
* Comparison operators
* String operators
* Logical operators
* Increment / decrement operators

---

### 2. **What are the assignment operators in PHP?**

Used to assign values to variables.

| Operator | Example    | Meaning           |
| -------- | ---------- | ----------------- |
| `=`      | `$x = 5;`  | Assign 5 to x     |
| `+=`     | `$x += 2;` | Add 2 to x        |
| `-=`     | `$x -= 3;` | Subtract 3 from x |
| `*=`     | `$x *= 4;` | Multiply x by 4   |
| `/=`     | `$x /= 2;` | Divide x by 2     |
| `%=`     | `$x %= 3;` | x = x mod 3       |

---

### 3. **What are the arithmetic operators in PHP?**

Used for math calculations.

| Operator | Description         | Example   |
| -------- | ------------------- | --------- |
| `+`      | Addition            | `$a + $b` |
| `-`      | Subtraction         | `$a - $b` |
| `*`      | Multiplication      | `$a * $b` |
| `/`      | Division            | `$a / $b` |
| `%`      | Modulus (remainder) | `$a % $b` |

---

### 4. **What are the comparison operators in PHP?**

Used to compare values (return true or false).

| Operator | Meaning                       | Example     |
| -------- | ----------------------------- | ----------- |
| `==`     | Equal                         | `$a == $b`  |
| `===`    | Identical (equal + same type) | `$a === $b` |
| `!=`     | Not equal                     | `$a != $b`  |
| `!==`    | Not identical                 | `$a !== $b` |
| `>`      | Greater than                  | `$a > $b`   |
| `<`      | Less than                     | `$a < $b`   |
| `>=`     | Greater than or equal         | `$a >= $b`  |
| `<=`     | Less than or equal            | `$a <= $b`  |

---

### 5. **What are the string operators in PHP?**

Used to join (concatenate) strings.

| Operator | Description   | Example                             |
| -------- | ------------- | ----------------------------------- |
| `.`      | Concatenation | `$a . $b`                           |
| `.=`     | Append        | `$a .= $b` (same as `$a = $a . $b`) |

#### Example:

```php
$a = "Hello";
$b = " World";
echo $a . $b;  // Output: Hello World
```

---

### 6. **What are the logical operators in PHP?**

Used with conditions (true or false).

| Operator | Meaning | Example               |    |            |   |             |
| -------- | ------- | --------------------- | -- | ---------- | - | ----------- |
| `&&`     | AND     | `($a > 5 && $b < 10)` |    |            |   |             |
| \`       |         | \`                    | OR | \`(\$a > 5 |   | \$b < 10)\` |
| `!`      | NOT     | `!($a == $b)`         |    |            |   |             |

---

### 7. **What is the difference between post-increment and pre-increment in PHP?**

* **Post-increment**: `$x++`
  → returns the current value, then increases by 1
* **Pre-increment**: `++$x`
  → increases by 1 first, then returns the new value

#### Example:

```php
$x = 5;
echo $x++;  // prints 5, $x becomes 6 after
echo ++$x;  // $x becomes 7, prints 7
```

---

### 8. **What is the difference between post-decrement and pre-decrement in PHP?**

Same idea, but decreasing.

* **Post-decrement**: `$x--` → return, then subtract
* **Pre-decrement**: `--$x` → subtract, then return

#### Example:

```php
$x = 5;
echo $x--;  // prints 5, then $x becomes 4
echo --$x;  // $x becomes 3, prints 3
```

---

### 9. **What is the meaning of loosely typed in PHP?**

PHP is **loosely typed**, meaning:

* You **don’t need to declare** the data type of variables.
* PHP automatically understands the type (string, number, etc.) based on the value.

#### Example:

```php
$x = 10;       // integer
$x = "hello";  // now it's a string
```

Same variable, no problem.

---

### 10. **Can we add strings and numbers in PHP?**

Yes, but the result depends on the context.

#### Example 1 – string starts with a number:

```php
echo 5 + "3 cats";  // Output: 8 (PHP reads the 3)
```

#### Example 2 – string doesn’t start with number:

```php
echo 5 + "cats";    // Output: 5 (string ignored, warning may appear)
```

So: PHP tries to convert the string to number if possible.

---

### 11. **How to combine multiple conditions together in PHP?**

Use **logical operators**:

```php
if ($age > 18 && $has_id) {
  echo "Allowed";
}
```

* `&&` = both must be true
* `||` = at least one must be true
* `!` = not

---

### 12. **What are comments?**

Comments are notes inside your code that PHP ignores.
They help you explain your code to yourself or others.

---

### 13. **How to write comments in PHP?**

There are two types:

#### Single-line comments:

```php
// This is a comment
# This is also a comment
```

#### Multi-line comments:

```php
/*
This is a
multi-line comment
*/
```

---

### 14. **Single line comments vs. multi-line comments**

| Type        | Symbol(s)   | Use For          |
| ----------- | ----------- | ---------------- |
| Single-line | `//` or `#` | One line comment |
| Multi-line  | `/* ... */` | Several lines    |

