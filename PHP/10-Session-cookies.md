
### 1. What are cookies and sessions in PHP?

* **Cookies:** Small pieces of data stored on the user's browser. They persist between requests and can have an expiration time.
* **Sessions:** Data stored on the server linked to a unique session ID (usually saved in a cookie). Sessions persist during the browser session and are used to keep user data secure.

---

### 2. How to set a cookie in PHP?

Use `setcookie()` function before any output.

```php
setcookie("user", "John", time() + 3600);  // expires in 1 hour
```

---

### 3. How to get the cookies in PHP?

Access the `$_COOKIE` superglobal.

```php
echo $_COOKIE['user'] ?? 'No cookie set';
```

---

### 4. How to unset (delete) a cookie in PHP?

Set cookie expiration time in the past.

```php
setcookie("user", "", time() - 3600);
```

---

### 5. What is the usage of `setcookie` function in PHP?

To create or modify a cookie with parameters: name, value, expiration, path, domain, secure, httponly.

---

### 6. What is usage of `$_COOKIE` superglobal variable in PHP?

To access all cookies sent by the browser.

---

### 7. How to set a new session in PHP?

Call `session_start()` then assign values to `$_SESSION`.

```php
session_start();
$_SESSION['user'] = "John";
```

---

### 8. How to get the session id in PHP?

Use `session_id()`.

```php
echo session_id();
```

---

### 9. How to destroy a session in PHP?

Use `session_destroy()` after `session_start()`.

```php
session_start();
session_destroy();
```

---

### 10. How to pass values between files using sessions in PHP?

Start session on both files, use `$_SESSION` to store/access data.

---

### 11. How to unset all session elements in PHP?

Use `session_unset()` after `session_start()`.

```php
session_start();
session_unset();
```

---

### 12. How to set a specific element in the session in PHP?

Assign value to `$_SESSION['key']`.

```php
$_SESSION['user'] = "John";
```

---

### 13. How to unset a specific element from the session in PHP?

Use `unset($_SESSION['key'])`.

---

### 14. What is usage of `$_SESSION` superglobal variable in PHP?

To store and retrieve session variables.

---

### 15. What is the usage of `session_start`, `session_id`, `session_destroy`, `session_abort`, and `session_unset` functions in PHP?

* `session_start()` — starts/resumes a session.
* `session_id()` — gets/sets the session ID.
* `session_destroy()` — destroys all session data.
* `session_abort()` — discards session changes.
* `session_unset()` — frees all session variables.

---

### 16. How to check if the user is logged in or not in PHP?

Check if a session variable like `$_SESSION['user']` exists.

```php
if (isset($_SESSION['user'])) {
  // user logged in
}
```

---

### 17. How to prevent logged users from accessing login and register pages in PHP?

Check login status at top, redirect if logged in.

```php
session_start();
if (isset($_SESSION['user'])) {
  header("Location: dashboard.php");
  exit;
}
```

---

### 18. How to prevent un-logged users from accessing pages that require login in PHP?

Check login status, redirect to login if not logged in.

```php
session_start();
if (!isset($_SESSION['user'])) {
  header("Location: login.php");
  exit;
}
```

---

### 19. How to navigate (redirect) to another page in PHP?

Use the `header` function with `Location:` and then `exit()`.

```php
header("Location: page.php");
exit();
```

---

### 20. What is the usage of `header` function in PHP?

Sends raw HTTP headers to the client. Used for redirects, content type, cache control, etc.

---

### 21. How to logout from the website and destroy the login detail stored in the session in PHP?

```php
session_start();
session_unset();
session_destroy();
header("Location: login.php");
exit();
```

---

### 22. How to prevent re-submission of POST requests (forms) in PHP?

Use **POST-Redirect-GET (PRG)** pattern: after handling POST, redirect user to another page.

---

### 23. What is POST-Redirect-GET pattern?

It avoids form re-submission when user refreshes by redirecting after POST submission to a GET page.

---

### 24. How to apply POST-Redirect-GET pattern in PHP?

After processing POST data, redirect using header().

```php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
  // process form
  header("Location: success.php");
  exit();
}
```

---

### 25. What are flash messages in PHP?

Temporary messages (success, errors) stored in session, shown once and then removed.

---

### 26. How to apply flash message in PHP?

Set message in session, show and unset it on next page load.

```php
// Set flash
$_SESSION['flash'] = "Registration successful.";

// Show flash
if (isset($_SESSION['flash'])) {
  echo $_SESSION['flash'];
  unset($_SESSION['flash']);
}
```

---

## Login system with cookies, sessions, login checks, redirect, and flash messages

```php
<?php
session_start();

// Flash message helper function
function setFlash($msg) {
    $_SESSION['flash'] = $msg;
}

function showFlash() {
    if (isset($_SESSION['flash'])) {
        echo "<p style='color:green'>" . $_SESSION['flash'] . "</p>";
        unset($_SESSION['flash']);
    }
}

// Redirect if logged in
if (isset($_SESSION['user'])) {
    header("Location: dashboard.php");
    exit();
}

// Login form submitted
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $username = $_POST['username'] ?? '';
    $password = $_POST['password'] ?? '';

    // Dummy auth check
    if ($username === 'admin' && $password === '123456') {
        $_SESSION['user'] = $username;

        // Set cookie for 1 day
        setcookie("user", $username, time() + 86400);

        setFlash("Welcome back, $username!");
        header("Location: dashboard.php");
        exit();
    } else {
        setFlash("Invalid username or password");
    }
}
?>

<form method="POST" action="">
    Username: <input type="text" name="username"><br>
    Password: <input type="password" name="password"><br>
    <input type="submit" value="Login">
</form>

<?php showFlash(); ?>
```

```php
// dashboard.php
<?php
session_start();
if (!isset($_SESSION['user'])) {
    header("Location: login.php");
    exit();
}

echo "Hello, " . htmlspecialchars($_SESSION['user']);

// Logout link
echo '<br><a href="logout.php">Logout</a>';
```

```php
// logout.php
<?php
session_start();
session_unset();
session_destroy();
setcookie("user", "", time() - 3600);  // Delete cookie

header("Location: login.php");
exit();
```


