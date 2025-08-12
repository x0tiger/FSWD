
### 1. What are the different superglobal variables in PHP?

Superglobals are predefined variables accessible everywhere, without needing `global` keyword. Main ones:

* `$_SERVER`
* `$_GET`
* `$_POST`
* `$_REQUEST`
* `$_FILES`
* `$_COOKIE`
* `$_SESSION`
* `$_ENV`
* `$GLOBALS`

---

### 2. What is the difference between variables and superglobal variables in PHP?

* **Normal variables**: Defined by the user, limited to function or file scope unless declared global.
* **Superglobals**: Built-in PHP arrays available everywhere automatically.

---

### 3. What is the usage of `$_SERVER` superglobal variable in PHP?

`$_SERVER` holds info about server and request environment like URL, headers, script path, client IP, request method, etc.

**Example:**

```php
echo $_SERVER['REQUEST_METHOD']; // GET or POST
echo $_SERVER['REMOTE_ADDR'];    // Client IP
```

---

### 4. What is the difference between GET and POST requests?

* **GET**: Sends data in URL query string, limited size, visible in URL, used for fetching.
* **POST**: Sends data in HTTP body, no size limit, hidden, used for submitting forms securely.

---

### 5. How to access the different values of the superglobal variables in PHP?

Use their keys inside square brackets.

**Example:**

```php
$name = $_GET['name'];
$age = $_POST['age'];
```

---

### 6. What is the benefit of "REQUEST\_METHOD" in PHP?

`$_SERVER['REQUEST_METHOD']` tells you if the request is GET, POST, or other, so you can handle logic accordingly.

---

### 7. What is the usage of `$_GET` superglobal variable in PHP?

Stores data sent via GET request (URL query parameters).

**Example:**

```php
// URL: page.php?user=Ahmed
echo $_GET['user']; // Output: Ahmed
```

---

### 8. What is the usage of `$_POST` superglobal variable in PHP?

Stores data sent via POST request (usually form data).

---

### 9. What is the usage of `$_REQUEST` superglobal variable in PHP?

Contains merged data from GET, POST, and COOKIE (in that order). Useful but less secure.

---

### 10. What is the usage of `$_FILES` superglobal variable in PHP?

Used to handle file uploads in forms.

**Example:**

```php
echo $_FILES['profile']['name']; // Uploaded file name
```

---

### 11. What is the meaning of an empty "action" attribute in HTML forms?

Means the form submits to the same page URL.

---

### 12. How to send query parameters with the POST request in HTML forms?

Add them in the form action URL.

**Example:**

```html
<form method="POST" action="submit.php?ref=123">
```

---

### 13. What will happen if the same key is used in `$_GET` and `$_POST` in PHP?

In `$_REQUEST`, POST values override GET values if the same key exists. In `$_GET` and `$_POST` separately, keys keep their own values.

---

### 14. What is the usage of `$GLOBALS` superglobal variable in PHP?

Contains all global variables as an associative array, accessible everywhere.

**Example:**

```php
$a = 5;
function test() {
  echo $GLOBALS['a']; // Accesses global $a
}
test();
```

---

### 15. How to access the outer scope variables inside functions in PHP?

* Use `global` keyword inside the function.
* Or use `$GLOBALS` array.

**Example:**

```php
$name = "Omar";

function sayName() {
  global $name;
  echo $name;
}

sayName(); // Output: Omar
```

---

## Example combining superglobals:

```php
<?php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $name = $_POST['name'] ?? 'Guest';
    echo "Hello, $name!<br>";
    
    if (isset($_FILES['avatar'])) {
        $fileName = $_FILES['avatar']['name'];
        echo "Uploaded file: $fileName<br>";
    }
} else {
    $ref = $_GET['ref'] ?? 'none';
    echo "You came from ref: $ref<br>";
}
?>

<form method="POST" action="?ref=homepage">
  Name: <input type="text" name="name"><br>
  Avatar: <input type="file" name="avatar"><br>
  <input type="submit" value="Submit">
</form>
```

