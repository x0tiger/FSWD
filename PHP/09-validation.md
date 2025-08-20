
### 1. Validating a register form using PHP

You check each input field against rules like required, format, length, matching passwords, etc., on the server side after form submission.

---

### 2. Applying validation on first name, last name, username, password, re-type password, email, bio, birth date, and gender using PHP

Typical validations:

* **First/Last name:** required, letters only, reasonable length
* **Username:** required, min/max length, allowed chars
* **Password:** required, min length, complexity
* **Re-type password:** must match password
* **Email:** required, valid email format
* **Bio:** optional, max length
* **Birth date:** valid date, maybe minimum age check
* **Gender:** must be one of predefined options

---

### 3. What is the difference between validation and sanitizing?

* **Validation:** Checking if input data meets certain rules (e.g., format, length) — is it valid?
* **Sanitizing:** Cleaning input data by removing or encoding unwanted characters to prevent security issues.

---

### 4. How to use `filter_var` function in PHP?

Used to validate or sanitize data based on filter types.

**Example:**

```php
$email = "test@example.com";
if (filter_var($email, FILTER_VALIDATE_EMAIL)) {
    echo "Valid email";
} else {
    echo "Invalid email";
}
```

---

### 5. How to use predefined PHP validation filters?

Use constants like `FILTER_VALIDATE_EMAIL`, `FILTER_VALIDATE_INT`, `FILTER_VALIDATE_URL`, etc., with `filter_var`.

---

### 6. How to use predefined PHP sanitizing filters?

Use constants like `FILTER_SANITIZE_STRING` (deprecated, use htmlspecialchars or strip\_tags instead), `FILTER_SANITIZE_EMAIL`, `FILTER_SANITIZE_URL`, etc.

---

### 7. What is HTML injection in PHP?

It’s when a user inputs HTML or JavaScript code that gets outputted and executed in the browser, potentially causing XSS (Cross-site scripting) attacks.

---

### 8. How to prevent HTML injection in PHP?

Use `htmlspecialchars()` to encode special HTML characters before outputting user input.

**Example:**

```php
echo htmlspecialchars($user_input, ENT_QUOTES, 'UTF-8');
```

---

### 9. How to compare strings using `strcmp` in PHP?

`strcmp($str1, $str2)` compares two strings exactly. Returns:

* 0 if equal
* <0 if `$str1` < `$str2`
* > 0 if `$str1` > `$str2`

---

## Full example: Register form validation with sanitization in PHP

```php
<?php
$errors = [];
$data = [
    'first_name' => '',
    'last_name' => '',
    'username' => '',
    'password' => '',
    're_password' => '',
    'email' => '',
    'bio' => '',
    'birth_date' => '',
    'gender' => ''
];

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    // Sanitize inputs
    $data['first_name'] = trim(filter_var($_POST['first_name'] ?? '', FILTER_SANITIZE_STRING));
    $data['last_name'] = trim(filter_var($_POST['last_name'] ?? '', FILTER_SANITIZE_STRING));
    $data['username'] = trim($_POST['username'] ?? '');
    $data['password'] = $_POST['password'] ?? '';
    $data['re_password'] = $_POST['re_password'] ?? '';
    $data['email'] = trim(filter_var($_POST['email'] ?? '', FILTER_SANITIZE_EMAIL));
    $data['bio'] = trim(htmlspecialchars($_POST['bio'] ?? '', ENT_QUOTES, 'UTF-8'));
    $data['birth_date'] = $_POST['birth_date'] ?? '';
    $data['gender'] = $_POST['gender'] ?? '';

    // Validate first name
    if (empty($data['first_name'])) {
        $errors[] = "First name is required.";
    } elseif (!preg_match("/^[a-zA-Z]+$/", $data['first_name'])) {
        $errors[] = "First name must contain letters only.";
    }

    // Validate last name
    if (empty($data['last_name'])) {
        $errors[] = "Last name is required.";
    } elseif (!preg_match("/^[a-zA-Z]+$/", $data['last_name'])) {
        $errors[] = "Last name must contain letters only.";
    }

    // Validate username
    if (empty($data['username'])) {
        $errors[] = "Username is required.";
    } elseif (strlen($data['username']) < 6 || strlen($data['username']) > 30) {
        $errors[] = "Username must be between 6 and 30 characters.";
    }

    // Validate password
    if (empty($data['password'])) {
        $errors[] = "Password is required.";
    } elseif (strlen($data['password']) < 6) {
        $errors[] = "Password must be at least 6 characters.";
    }

    // Validate re-typed password
    if (strcmp($data['password'], $data['re_password']) !== 0) {
        $errors[] = "Passwords do not match.";
    }

    // Validate email
    if (empty($data['email'])) {
        $errors[] = "Email is required.";
    } elseif (!filter_var($data['email'], FILTER_VALIDATE_EMAIL)) {
        $errors[] = "Invalid email format.";
    }

    // Validate bio length (optional)
    if (strlen($data['bio']) > 500) {
        $errors[] = "Bio must be less than 500 characters.";
    }

    // Validate birth date (basic)
    if (!empty($data['birth_date']) && !DateTime::createFromFormat('Y-m-d', $data['birth_date'])) {
        $errors[] = "Invalid birth date format. Use YYYY-MM-DD.";
    }

    // Validate gender
    $allowed_genders = ['male', 'female', 'other'];
    if (!in_array($data['gender'], $allowed_genders)) {
        $errors[] = "Please select a valid gender.";
    }
}
?>

<form method="POST" action="">
    First Name: <input type="text" name="first_name" value="<?= htmlspecialchars($data['first_name']) ?>"><br>
    Last Name: <input type="text" name="last_name" value="<?= htmlspecialchars($data['last_name']) ?>"><br>
    Username: <input type="text" name="username" value="<?= htmlspecialchars($data['username']) ?>"><br>
    Password: <input type="password" name="password"><br>
    Re-type Password: <input type="password" name="re_password"><br>
    Email: <input type="email" name="email" value="<?= htmlspecialchars($data['email']) ?>"><br>
    Bio: <textarea name="bio"><?= htmlspecialchars($data['bio']) ?></textarea><br>
    Birth Date: <input type="date" name="birth_date" value="<?= htmlspecialchars($data['birth_date']) ?>"><br>
    Gender: 
    <select name="gender">
        <option value="">Select</option>
        <option value="male" <?= $data['gender']=='male' ? 'selected' : '' ?>>Male</option>
        <option value="female" <?= $data['gender']=='female' ? 'selected' : '' ?>>Female</option>
        <option value="other" <?= $data['gender']=='other' ? 'selected' : '' ?>>Other</option>
    </select><br>
    <input type="submit" value="Register">
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


