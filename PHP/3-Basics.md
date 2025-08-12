
### 1. **What are conditional blocks in PHP?**

Conditional blocks are pieces of code that run only if a certain condition is true. They let your program **make decisions**.

---

### 2. **What are the different types of conditional blocks in PHP?**

* `if`
* `if-else`
* `if-elseif-else`
* `switch`

---

### 3. **Recap on the conditional and logical operators**

* Conditional operators compare values:
  `==`, `!=`, `>`, `<`, `>=`, `<=`, `===`, `!==`
* Logical operators combine conditions:
  `&&` (AND), `||` (OR), `!` (NOT)

---

### 4. **What is a condition in PHP?**

A condition is an expression that returns `true` or `false`.

Example:

```php
$age = 20;
$age > 18   // This is a condition, it returns true here
```

---

### 5. **What is the usage of "if" block in PHP?**

Runs code only if the condition is true.

```php
if ($age > 18) {
  echo "You are an adult.";
}
```

If `$age > 18` is true, it runs the echo line.

---

### 6. **What is the usage of "if-else" block in PHP?**

Runs one block if condition is true, else runs another block.

```php
if ($age > 18) {
  echo "Adult";
} else {
  echo "Not adult";
}
```

---

### 7. **What is the usage of "if-elseif-else" block in PHP?**

Used for multiple conditions.

```php
if ($age < 13) {
  echo "Child";
} elseif ($age < 20) {
  echo "Teenager";
} else {
  echo "Adult";
}
```

---

### 8. **What is the usage of "switch" block in PHP?**

Used to check one variable against many possible values.

```php
$color = "red";

switch ($color) {
  case "red":
    echo "Color is red";
    break;
  case "blue":
    echo "Color is blue";
    break;
  default:
    echo "Color not found";
}
```

---

### 9. **What is the usage of "default" and "break" in the "switch" block in PHP?**

* `break` stops the switch after a match, so it doesn’t check other cases.
* `default` runs if no case matches.

---

### 10. **Combining logical and conditional operators in PHP**

You can mix them to make complex conditions.

```php
if ($age > 18 && $country == "Egypt") {
  echo "Adult from Egypt";
}
```

---

### 11. **How to combine the statements of multiple cases in the "switch" block in PHP?**

If you want one block to run for multiple cases, write cases one after another without `break`.

```php
switch ($day) {
  case "Saturday":
  case "Sunday":
    echo "Weekend";
    break;
  default:
    echo "Weekday";
}
```

---

### 12. **What is the conditional operators in PHP?**

These are operators like:

* `==`, `!=`, `>`, `<`, `>=`, `<=`, `===`, `!==`

They compare two values and return true or false.

---

### 13. **What is the ternary operator in PHP?**

Short way to write an if-else.

```php
echo ($age > 18) ? "Adult" : "Not adult";
```

It means: if `$age > 18` true → print "Adult", else print "Not adult".

---

### 14. **What is the null coalescing operator in PHP?**

Used to check if a variable exists and is not null, otherwise use a default.

```php
$name = $_GET['name'] ?? 'Guest';
```

If `$_GET['name']` is set, `$name` gets it, else `$name` is "Guest".
