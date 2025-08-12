

### 1. What is SQL injection?

SQL injection is a security vulnerability where an attacker can insert or “inject” malicious SQL code into a query, which can lead to unauthorized access, data leakage, or data destruction.

Example: If you directly use user input inside a query without validation or escaping, attackers can manipulate the SQL command.

---

### 2. Demo on SQL injection to delete the database.

Suppose you have this vulnerable code:

```php
$id = $_GET['id'];
$sql = "DELETE FROM cities WHERE id = $id";
$pdo->exec($sql);
```

If attacker sends: `id=1; DROP DATABASE world; --`

The executed SQL becomes:

```sql
DELETE FROM cities WHERE id = 1; DROP DATABASE world; -- 
```

This will delete the entire database.

---

### 3. How to prevent SQL injection?

* Use **prepared statements** with bound parameters.
* Validate and sanitize user input.
* Use PDO or MySQLi prepared queries.

---

### 4. Recap on HTML injection and how to prevent it.

HTML injection is when user inputs malicious HTML or JavaScript, causing Cross-Site Scripting (XSS).

**Prevention:** Use `htmlspecialchars()` or other escaping functions when outputting user input.

---

### 5. How to prepare a SQL statement in PHP?

Using PDO:

```php
$stmt = $pdo->prepare("DELETE FROM cities WHERE id = ?");
```

---

### 6. What is usage of "prepare" and "execute" PDO functions in PHP?

* `prepare`: Prepares an SQL statement for execution, allowing placeholders.
* `execute`: Executes the prepared statement with actual values.

This separates query from data, preventing SQL injection.

---

### 7. How to delete a city from the "world" database using PHP?

```php
$id = $_POST['id'] ?? null;
if ($id) {
    $stmt = $pdo->prepare("DELETE FROM City WHERE ID = ?");
    $stmt->execute([$id]);
    echo "City deleted successfully.";
}
```

---

### 8. How to add a confirmation on deletion events using JavaScript?

Add `onclick` attribute to confirm:

```html
<form method="POST" onsubmit="return confirm('Are you sure you want to delete this city?');">
  <input type="hidden" name="id" value="123">
  <button type="submit">Delete</button>
</form>
```

---

### 9. Displaying a success flashing message on deletion success.

Use PHP session or simple message display after action:

```php
if ($deleted) {
    echo "<div class='success'>City deleted successfully!</div>";
}
```

You can also use session flash messages.

---

### 10. Comparison between "prepare", "exec" and "query" PDO functions in PHP.

| Function  | Usage                                          | Returns                 | Notes                      |
| --------- | ---------------------------------------------- | ----------------------- | -------------------------- |
| `prepare` | Prepares statement with placeholders           | PDOStatement            | Use with `execute()`       |
| `execute` | Executes a prepared statement                  | bool                    | Needs prepared statement   |
| `exec`    | Executes a simple SQL (INSERT, UPDATE, DELETE) | Number of affected rows | Does not return result set |
| `query`   | Executes an SQL that returns results (SELECT)  | PDOStatement            | Use to fetch data          |

---

## Advanced Example: Secure city deletion with confirmation and flash message

```php
<?php
session_start();

try {
    $pdo = new PDO("mysql:host=localhost;dbname=world;charset=utf8", "root", "");
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['id'])) {
        $stmt = $pdo->prepare("DELETE FROM City WHERE ID = ?");
        $stmt->execute([$_POST['id']]);
        $_SESSION['flash_message'] = "City deleted successfully!";
        header("Location: cities.php");
        exit;
    }

    // Fetch cities
    $stmt = $pdo->query("SELECT ID, Name FROM City ORDER BY Name");
    $cities = $stmt->fetchAll(PDO::FETCH_ASSOC);
} catch (PDOException $e) {
    die("DB Error: " . $e->getMessage());
}
?>

<!DOCTYPE html>
<html>
<head><title>Cities</title></head>
<body>

<?php
if (!empty($_SESSION['flash_message'])) {
    echo "<div style='color:green;'>" . htmlspecialchars($_SESSION['flash_message']) . "</div>";
    unset($_SESSION['flash_message']);
}
?>

<ul>
    <?php foreach ($cities as $city): ?>
        <li>
            <?= htmlspecialchars($city['Name']) ?>
            <form method="POST" style="display:inline;" onsubmit="return confirm('Delete this city?');">
                <input type="hidden" name="id" value="<?= $city['ID'] ?>">
                <button type="submit">Delete</button>
            </form>
        </li>
    <?php endforeach; ?>
</ul>

</body>
</html>
```

