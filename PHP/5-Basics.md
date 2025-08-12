

### 1. What are arrays in programming?

Arrays are special variables that store multiple values under one name, ordered by index or key.

**Explanation:**
Instead of many separate variables, arrays let you group related data. Each item in an array can be accessed by its position (index) or key.

**Example:**

```php
$fruits = ["apple", "banana", "orange"];
```

---

### 2. How to create an array in PHP?

Use square brackets `[]` or the `array()` function.

**Explanation:**
Both ways create arrays, but `[]` is more modern and easier.

**Example:**

```php
// Using []
$numbers = [1, 2, 3];

// Using array()
$letters = array("a", "b", "c");
```

---

### 3. What are the different types of arrays in PHP?

* Indexed arrays
* Associative arrays
* Multidimensional arrays

**Explanation:**

* Indexed arrays use numbers as keys.
* Associative arrays use custom keys (like strings).
* Multidimensional arrays are arrays inside arrays.

---

### 4. How to create an indexed array in PHP?

Use numeric indexes automatically or assign them.

**Example:**

```php
// Automatic index starting at 0
$colors = ["red", "green", "blue"];

// Manual index
$colors = [0 => "red", 1 => "green", 2 => "blue"];
```

---

### 5. What is the meaning of zero-indexed array?

An array where the first element is at index 0.

**Explanation:**
Counting starts at 0, so `$arr[0]` is the first element.

---

### 6. What is the meaning of zero-indexed language?

Programming language where array indexes start at 0.

---

### 7. What is the first index of an array in PHP?

Always 0 for indexed arrays.

---

### 8. How to access a specific value of an array in PHP?

Use the index or key inside square brackets.

**Example:**

```php
echo $colors[1]; // Output: green
```

---

### 9. How to change a specific value of an array in PHP?

Assign a new value to the index/key.

**Example:**

```php
$colors[1] = "yellow";
echo $colors[1]; // Output: yellow
```

---

### 10. Can we store different data types in arrays in PHP?

Yes, PHP arrays can hold any mix of types.

**Example:**

```php
$arr = [1, "two", 3.0, true];
```

---

### 11. How to create an associative array in PHP?

Use keys (strings) with `=>` syntax.

**Example:**

```php
$user = [
  "name" => "Ahmed",
  "age" => 30,
  "city" => "Cairo"
];
```

---

### 12. What is the difference between indexed and associative arrays in PHP?

* Indexed arrays use numeric keys starting at 0.
* Associative arrays use custom keys (usually strings).

---

### 13. How to create a multidimensional array in PHP?

Create arrays inside arrays.

**Example:**

```php
$matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];
```

---

### 14. How to use negative string indexing in PHP?

You can use negative numbers with some string functions, but PHP arrays don’t support negative indexes directly.

**Explanation:**
To access string chars from the end, PHP lets you use negative offsets like `$str[-1]` for last char.

---

### 15. What is the usage of these PHP functions?

* `array_push($arr, $val)`: add `$val` to end
* `array_pop($arr)`: remove last element
* `array_reverse($arr)`: return reversed array
* `array_unshift($arr, $val)`: add `$val` to start
* `array_shift($arr)`: remove first element
* `in_array($val, $arr)`: check if `$val` exists
* `count($arr)`: count elements
* `array_unique($arr)`: remove duplicate values
* `array_sum($arr)`: sum elements (numbers)
* `array_product($arr)`: multiply elements
* `shuffle($arr)`: randomize order (in-place)
* `end($arr)`: get last element

---

### 16. How to append an element to the array using "\[]" in PHP?

Use `$arr[] = $val;` to add at the end.

**Example:**

```php
$colors = ["red", "green"];
$colors[] = "blue";
print_r($colors);
// Output: Array ( [0] => red [1] => green [2] => blue )
```

---

##  Example combining arrays:

```php
$people = [
  ["name" => "Ali", "age" => 25],
  ["name" => "Sara", "age" => 30],
  ["name" => "Omar", "age" => 22]
];

// Add new person
$people[] = ["name" => "Mona", "age" => 27];

// Print all names older than 23
foreach ($people as $person) {
  if ($person["age"] > 23) {
    echo $person["name"] . " ";
  }
}
// Output: Ali Sara Mona

// Reverse the array and show names
$reversed = array_reverse($people);
foreach ($reversed as $person) {
  echo $person["name"] . " ";
}
// Output: Mona Omar Sara Ali
```


