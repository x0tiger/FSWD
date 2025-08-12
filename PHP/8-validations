

### 1. Applying validations on a login form using PHP

You check the submitted form data and validate rules like "required", "length" etc. in PHP after the form is submitted.

---

### 2. Applied validations: required, >= 6 chars, <= 100 chars.

* **Required:** Input must not be empty.
* **Minimum length:** Input length should be at least 6 characters.
* **Maximum length:** Input length should be at most 100 characters.

---

### 3. Restricting the validations on the POST request only

Only run validation code if the form was submitted via POST, to avoid errors when page first loads or GET requests.

**Example:**

```php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
  // Validate here
}
```

---

### 4. What is the usage of `isset` function in PHP?

`isset()` checks if a variable is set and not `null`. Useful to check if form input exists before using it.

**Example:**

```php
if (isset($_POST['username'])) {
  $username = $_POST['username'];
}
```

---

### 5. What is the usage of `strlen` function in PHP?

Returns the length (number of characters) of a string.

**Example:**

```php
$len = strlen("Hello"); // $len = 5
```

---

### 6. How to collect the validation errors in a single PHP array?

Create an empty array `$errors` and add error messages to it when validations fail.

**Example:**

```php
$errors = [];

if (empty($username)) {
  $errors[] = "Username is required.";
}
if (strlen($username) < 6) {
  $errors[] = "Username must be at least 6 characters.";
}
```

---

### 7. How to display the validation errors in HTML?

Loop over the `$errors` array and print each error inside HTML tags (e.g. list items).

**Example:**

```php
if (!empty($errors)) {
  echo "<ul>";
  foreach ($errors as $error) {
    echo "<li>$error</li>";
  }
  echo "</ul>";
}
```

---

## Full example: Login form validation with PHP

```php
<?php
$errors = [];
$username = "";

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $username = $_POST['username'] ?? '';

    if (!isset($username) || trim($username) === '') {
        $errors[] = "Username is required.";
    } else {
        $len = strlen($username);
        if ($len < 6) {
            $errors[] = "Username must be at least 6 characters.";
        }
        if ($len > 100) {
            $errors[] = "Username must be less than or equal 100 characters.";
        }
    }
}
?>

<form method="POST" action="">
    Username: <input type="text" name="username" value="<?= htmlspecialchars($username) ?>"><br>
    <input type="submit" value="Login">
</form>

<?php
if (!empty($errors)) {
    echo "<ul style='color:red;'>";
    foreach ($errors as $error) {
        echo "<li>$error</li>";
    }
    echo "</ul>";
}
?>
```


