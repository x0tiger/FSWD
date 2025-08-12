

### 1. What is meaning of files and folders direct access in Web?

Direct access means someone types or tries to access a file or folder URL directly in the browser, like:

```
http://example.com/folder/
http://example.com/folder/file.php
```

Sometimes you want to restrict this to protect your app or hide implementation.

---

### 2. How to prevent folder direct access in PHP?

Put an `index.php` or `index.html` file inside the folder that either blocks or redirects access, so if someone enters the folder URL, they get a controlled response instead of a directory listing.

---

### 3. How to display blank pages on folder direct access in PHP?

Create an empty `index.php` file in the folder:

```php
<?php
// no output here
```

When accessing the folder URL, it shows a blank page.

---

### 4. How to redirect to another webpage on folder direct access in PHP?

Put this in `index.php` inside the folder:

```php
<?php
header("Location: /somepage.php");
exit;
```

---

### 5. How to redirect to a forbidden webpage on folder direct access in PHP?

Inside `index.php`:

```php
<?php
header("HTTP/1.1 403 Forbidden");
header("Location: /forbidden.php");
exit;
```

---

### 6. How to redirect to a forbidden webpage on file direct access in PHP?

Add this check at the top of the PHP file to detect if it’s directly accessed:

```php
<?php
if (basename(__FILE__) == basename($_SERVER['PHP_SELF'])) {
    header("HTTP/1.1 403 Forbidden");
    header("Location: /forbidden.php");
    exit;
}
```

---

### 7. How to get the current script filename in PHP?

Use `basename($_SERVER['PHP_SELF'])` or `__FILE__` magic constant.

---

### 8. What are PHP magic constants?

Predefined constants that change depending on where they are used. Some examples:

* `__FILE__` — full path and filename of the current file
* `__DIR__` — directory of the current file
* `__LINE__` — current line number

---

### 9. What is the usage "**FILE**" and "**DIR**" PHP magic constants?

* `__FILE__`: Gives the absolute path of the current PHP file.
* `__DIR__`: Gives the directory of the current PHP file.

Example:

```php
echo __FILE__; // /var/www/html/folder/file.php
echo __DIR__;  // /var/www/html/folder
```

---

### 10. What is the usage of "realpath" function in PHP?

It returns the absolute canonicalized path, resolving symbolic links and relative references like `..`.

Example:

```php
echo realpath('./file.php');
```

---

### 11. What are the different types of errors in PHP?

* **Parse errors:** Syntax errors, stop script execution.
* **Fatal errors:** Critical errors, script stops.
* **Warnings:** Non-fatal, script continues but warns you.
* **Notices:** Minor issues, script continues.

---

### 12. How to control error reporting using "error\_reporting" PHP function?

Use:

```php
error_reporting(E_ALL); // Show all errors
error_reporting(0);     // Turn off errors
```

---

### 13. How to throw exceptions in PHP?

Use `throw` keyword inside a function or code:

```php
throw new Exception("Error happened");
```

---

### 14. How to catch exception in PHP?

Use `try-catch` block:

```php
try {
    // code that might throw exception
} catch (Exception $e) {
    echo "Caught: " . $e->getMessage();
}
```

---

### 15. What are the different predefined exception classes in PHP?

* `Exception` (base class)
* `ErrorException`
* `PDOException`
* `InvalidArgumentException`
* `LogicException`, etc.

---

### 16. How to use "try-catch-finally" block in PHP?

```php
try {
    // risky code
} catch (Exception $e) {
    // handle exception
} finally {
    // code runs always
}
```

---

## Example: Prevent direct access, use magic constants, and handle exceptions

```php
<?php
// Prevent direct access to this file
if (basename(__FILE__) == basename($_SERVER['PHP_SELF'])) {
    header("HTTP/1.1 403 Forbidden");
    exit("Forbidden access");
}

try {
    // Use magic constants
    echo "File: " . __FILE__ . "<br>";
    echo "Dir: " . __DIR__ . "<br>";

    // Some risky code
    if (!file_exists(__DIR__ . "/data.txt")) {
        throw new Exception("File not found");
    }

    $content = file_get_contents(__DIR__ . "/data.txt");
    echo nl2br(htmlspecialchars($content));

} catch (Exception $e) {
    echo "Error: " . $e->getMessage();
} finally {
    echo "<br>Execution finished.";
}
```
