

### 1. **What is the difference between single and double quotes in PHP?**

* **Single quotes `' '`**: take text as it is. Variables inside them **won’t be evaluated**.
* **Double quotes `" "`**: variables inside them **will be evaluated**.

#### Example:

```php
$name = "Ali";

echo 'Hello $name';  // Output: Hello $name
echo "Hello $name";  // Output: Hello Ali
```

---

### 2. **How to insert a variable in double quotes in PHP?**

You just write the variable inside the double quotes.

#### Example:

```php
$age = 20;
echo "I am $age years old.";
```

If it’s part of a longer word, use `{}` to be safe:

```php
$name = "Sara";
echo "Hello {$name}sister";
```

---

### 3. **How is concatenation performed in PHP?**

You use the `.` operator to join strings.

#### Example:

```php
$first = "Hello";
$second = "World";

echo $first . " " . $second;  // Output: Hello World
```

---

### 4. **How to get the built-in functions of strings in PHP?**

There are a lot of string functions in PHP. You can check them by:

* Going to the official PHP documentation: [https://www.php.net/manual/en/ref.strings.php](https://www.php.net/manual/en/ref.strings.php)
* Or just Google: `php string functions`

---

### 5. **Usages of common string functions in PHP**

Here’s a breakdown with examples:

#### `str_repeat($string, $times)`

Repeats a string.

```php
echo str_repeat("Ha", 3);  // Output: HaHaHa
```

#### `str_replace($search, $replace, $string)`

Replaces text.

```php
echo str_replace("cat", "dog", "The cat is here.");  // Output: The dog is here.
```

#### `lcfirst($string)`

Makes first character lowercase.

```php
echo lcfirst("Hello");  // hello
```

#### `ucfirst($string)`

Makes first character uppercase.

```php
echo ucfirst("hello");  // Hello
```

#### `ucwords($string)`

Capitalizes the first letter of each word.

```php
echo ucwords("hello world");  // Hello World
```

#### `ltrim($string)`

Removes spaces from the left.

```php
echo ltrim("  hello");  // "hello"
```

#### `rtrim($string)`

Removes spaces from the right.

```php
echo rtrim("hello  ");  // "hello"
```

#### `trim($string)`

Removes spaces from both sides.

```php
echo trim("  hello  ");  // "hello"
```

#### `htmlspecialchars($string)`

Converts special HTML characters to safe ones.

```php
echo htmlspecialchars("<h1>Hello</h1>");  // &lt;h1&gt;Hello&lt;/h1&gt;
```

#### `htmlspecialchars_decode($string)`

Reverts the effect of `htmlspecialchars`.

```php
echo htmlspecialchars_decode("&lt;b&gt;Hi&lt;/b&gt;");  // <b>Hi</b>
```

#### `str_shuffle($string)`

Shuffles characters randomly.

```php
echo str_shuffle("hello");  // e.g. "lohel"
```

#### `str_word_count($string)`

Counts number of words.

```php
echo str_word_count("Hello there world");  // 3
```

#### `explode($delimiter, $string)`

Splits a string into an array.

```php
print_r(explode(" ", "one two three"));
// Array ( [0] => one [1] => two [2] => three )
```

#### `implode($separator, $array)`

Joins array elements into a string.

```php
echo implode("-", ["2025", "08", "12"]);  // Output: 2025-08-12
```

#### `strlen($string)`

Returns length of the string.

```php
echo strlen("hello");  // 5
```

#### `substr($string, $start, $length)`

Returns part of a string.

```php
echo substr("hello", 1, 3);  // Output: ell
```

#### `strtoupper($string)`

Converts to uppercase.

```php
echo strtoupper("hello");  // HELLO
```

#### `strtolower($string)`

Converts to lowercase.

```php
echo strtolower("HELLO");  // hello
```

---

### 6. **What is the usage of `phpinfo()` function?**

`phpinfo()` shows all info about your PHP setup:

* PHP version
* Server info
* Loaded extensions
* Configuration

#### Example:

```php
phpinfo();
```

Put it in a file like `info.php` and open it in browser.

---

### 7. **How to get the current version of PHP?**

Use:

```php
echo phpversion();
```

This will print the current PHP version running.

---

### 8. **What are the different special characters in PHP?**

Special characters inside strings:

* `\n` → new line
* `\t` → tab
* `\\` → backslash
* `\"` → double quote
* `\$` → dollar sign
* `\r` → carriage return

They only work inside **double quotes**, not single quotes.

---

### 9. **What is the usage of `nl2br()` function in PHP?**

It converts new line characters (`\n`) into HTML `<br>` tags.

Useful when showing multi-line text in HTML.

#### Example:

```php
$text = "Hello\nWorld";
echo nl2br($text);
// Output: Hello<br>World
```

---

### 10. **How to convert new lines to `<br>` tags in PHP?**

Just use:

```php
nl2br($string);
```

---

### 11. **How to convert `<br>` tags to new lines in PHP?**

Use `str_replace()`:

```php
$text = "Hello<br>World";
echo str_replace("<br>", "\n", $text);
```

