
### 1. What is a function?

A function is a reusable block of code that performs a specific task.

**Explanation:**
Functions help organize code, avoid repetition, and make programs easier to read and maintain.

**Example:**

```php
function sayHello() {
  echo "Hello!";
}
```

---

### 2. What is the benefit of using functions?

Functions let you reuse code, keep code organized, and make debugging easier.

**Explanation:**
Instead of writing the same code multiple times, you write it once in a function and call it wherever needed.

---

### 3. What are the different types of functions in PHP?

* Built-in functions (provided by PHP)
* User-defined functions (you write)
* Anonymous functions (functions without names)
* Arrow functions (short syntax for anonymous functions)
* Closures (anonymous functions with context)

---

### 4. How to write a function in PHP?

Use the `function` keyword followed by the function name and parentheses.

**Example:**

```php
function greet() {
  echo "Hi there!";
}
```

---

### 5. How to call a user-defined function in PHP?

Write the function name followed by parentheses.

**Example:**

```php
greet(); // Calls the function and outputs: Hi there!
```

---

### 6. What are the function arguments (parameters) in PHP?

Arguments are values you pass into functions to work with inside.

**Example:**

```php
function greet($name) {
  echo "Hello, $name!";
}
```

---

### 7. How to pass values to functions in PHP?

Put values inside parentheses when calling the function.

**Example:**

```php
greet("Ali"); // Output: Hello, Ali!
```

---

### 8. What is the difference between built-in and user-defined functions in PHP?

* Built-in: Functions provided by PHP (e.g. `strlen()`)
* User-defined: Functions you create yourself

---

### 9. How to set default values for functions arguments in PHP?

Assign a value when declaring the parameter.

**Example:**

```php
function greet($name = "Guest") {
  echo "Hello, $name!";
}
greet();         // Output: Hello, Guest!
greet("Sara");   // Output: Hello, Sara!
```

---

### 10. How to declare data types for the function arguments and return value in PHP?

Use type hints before parameters and after the closing parenthesis for return type.

**Example:**

```php
function add(int $a, int $b): int {
  return $a + $b;
}
echo add(3, 4); // Output: 7
```

---

### 11. What is the usage of "declare" directive in PHP?

`declare` controls how PHP executes code, like enabling strict typing.

**Example:**

```php
declare(strict_types=1);
```

---

### 12. What is the usage of "strict\_types" in PHP?

When set to 1, PHP enforces the exact data types for function arguments and return types.

**Explanation:**
Prevents PHP from auto-converting types, making code safer.

---

### 13. How to accept nulls for the function arguments in PHP?

Add `?` before the type to allow `null`.

**Example:**

```php
function greet(?string $name) {
  if ($name === null) {
    echo "Hello, Guest!";
  } else {
    echo "Hello, $name!";
  }
}
```

---

### 14. What is the usage of "void" as a function return datatype in PHP?

`void` means the function does not return any value.

**Example:**

```php
function sayHello(): void {
  echo "Hello!";
}
```

---

### 15. How to create a variadic function in PHP?

Use three dots `...` before the parameter name to accept multiple arguments as an array.

**Example:**

```php
function sum(...$numbers) {
  return array_sum($numbers);
}
echo sum(1, 2, 3); // Output: 6
```

---

### 16. What is usage of three dots "..." in PHP?

* In function parameters: gathers multiple arguments into an array (rest operator).
* In function calls: spreads arrays into arguments (spread operator).

---

### 17. What is the usage of spread operator in PHP?

It unpacks an array into individual arguments.

**Example:**

```php
function add($a, $b, $c) {
  return $a + $b + $c;
}
$nums = [1, 2, 3];
echo add(...$nums); // Output: 6
```

---

### 18. What is the meaning of unpacking in PHP?

Converting an array into individual values, usually for function arguments.

---

### 19. What is the usage of rest operator in PHP?

It collects multiple function arguments into one array.

---

### 20. How to unpack an array into another array in PHP?

Use `...` inside array brackets.

**Example:**

```php
$arr1 = [1, 2];
$arr2 = [...$arr1, 3, 4];
print_r($arr2); // Output: [1, 2, 3, 4]
```

---

### 21. What is usage of "array\_map" function in PHP?

Applies a callback function to every element in an array, returning a new array.

**Example:**

```php
$nums = [1, 2, 3];
$doubled = array_map(fn($n) => $n * 2, $nums);
print_r($doubled); // Output: [2, 4, 6]
```

---

### 22. What is a closure in PHP?

A closure is an anonymous function that can access variables outside its scope via `use`.

---

### 23. What is an anonymous function in PHP?

A function without a name, usually assigned to variables or passed as callbacks.

**Example:**

```php
$greet = function($name) {
  echo "Hi, $name!";
};
$greet("Ahmed");
```

---

### 24. What is usage of "use" keyword with functions in PHP?

`use` imports variables from the parent scope into anonymous functions.

**Example:**

```php
$name = "Omar";
$greet = function() use ($name) {
  echo "Hi, $name!";
};
$greet(); // Output: Hi, Omar!
```

---

### 25. How to access outer variables in functions in PHP?

Using `use` inside anonymous functions.

---

### 26. What are arrow functions in PHP?

Shorter syntax for anonymous functions, automatically importing outer variables by value.

---

### 27. How to write arrow functions in PHP?

Use `fn` keyword with a single expression.

**Example:**

```php
$add = fn($a, $b) => $a + $b;
echo $add(2, 3); // Output: 5
```

---

### 28. What is the difference between closures and arrow functions in PHP?

* Closures use `function` keyword and need `use` to access outer vars.
* Arrow functions use `fn` and automatically capture outer variables by value.

---

## Example combining many function concepts:

```php
declare(strict_types=1);

function multiply(int ...$nums): int {
    return array_product($nums);
}

$factor = 2;
$multiplier = fn($num) => $num * $factor;

$values = [1, 2, 3];
$doubled = array_map($multiplier, $values);

echo "Doubled: ";
print_r($doubled);

echo "Product: " . multiply(...$doubled);

$greet = function(?string $name = null): void {
    $msg = $name ? "Hello, $name!" : "Hello, Guest!";
    echo $msg;
};

$greet("Sara");
$greet();
```


