

### 1. How to create a connection with the DBMS using PHP?

You connect to a database using extensions like MySQLi or PDO. The connection requires host, username, password, and database name.

---

### 2. What is the difference between MySQL, MySQLi and PDO in PHP?

* **MySQL:** Old deprecated extension, don't use.
* **MySQLi:** Improved MySQL extension, supports object-oriented and procedural styles, supports prepared statements.
* **PDO (PHP Data Objects):** Database access abstraction layer supporting many DBMSs, supports prepared statements, more flexible and secure.

---

### 3. How to create a PDO connection with MySQL in PHP?

```php
try {
    $pdo = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "username", "password");
} catch (PDOException $e) {
    die("Connection failed: " . $e->getMessage());
}
```

---

### 4. How to change the PDO error mode and what are the different PDO error modes in PHP?

PDO error modes control how errors are handled.

```php
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);  // Throws exceptions on errors
```

Other modes:

* `PDO::ERRMODE_SILENT` — Default, just set error codes.
* `PDO::ERRMODE_WARNING` — Emit warnings.
* `PDO::ERRMODE_EXCEPTION` — Throw exceptions.

---

### 5. How to get table records and map them to HTML in PHP?

Fetch records using PDO’s `query()` or `prepare()` and loop through results to output HTML.

```php
$stmt = $pdo->query("SELECT * FROM users");
echo "<ul>";
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
    echo "<li>" . htmlspecialchars($row['name']) . "</li>";
}
echo "</ul>";
```

---

### 6. How to get dynamic records according to a GET (query) parameter in PHP?

Use prepared statements with bound parameters to avoid SQL injection.

```php
$id = $_GET['id'] ?? null;

if ($id) {
    $stmt = $pdo->prepare("SELECT * FROM users WHERE id = ?");
    $stmt->execute([$id]);
    $user = $stmt->fetch(PDO::FETCH_ASSOC);
}
```

---

### 7. Displaying the countries and cities using the "world" database in PHP.

Assuming you have the "world" database with `Country` and `City` tables, you can join and display countries with their cities.

```php
$sql = "SELECT Country.Name as country, City.Name as city 
        FROM Country 
        LEFT JOIN City ON Country.Code = City.CountryCode 
        ORDER BY Country.Name, City.Name";

$stmt = $pdo->query($sql);
$currentCountry = null;

echo "<ul>";
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
    if ($row['country'] !== $currentCountry) {
        if ($currentCountry !== null) {
            echo "</ul></li>";
        }
        $currentCountry = $row['country'];
        echo "<li>" . htmlspecialchars($currentCountry) . "<ul>";
    }
    echo "<li>" . htmlspecialchars($row['city']) . "</li>";
}
echo "</ul></li></ul>";
```

---

### 8. Displaying a warning if there are no records in HTML.

Check if records exist, if not show a message.

```php
$stmt = $pdo->query("SELECT * FROM users");
$rows = $stmt->fetchAll(PDO::FETCH_ASSOC);

if (count($rows) === 0) {
    echo "<p>No records found!</p>";
} else {
    foreach ($rows as $row) {
        echo "<p>" . htmlspecialchars($row['name']) . "</p>";
    }
}
```

---

### 9. Redirect if the required query parameter is not found in the table.

Check if a GET parameter exists and matches a record. If not, redirect.

```php
$id = $_GET['id'] ?? null;

if (!$id) {
    header("Location: error.php");
    exit;
}

$stmt = $pdo->prepare("SELECT * FROM users WHERE id = ?");
$stmt->execute([$id]);
$user = $stmt->fetch(PDO::FETCH_ASSOC);

if (!$user) {
    header("Location: error.php");
    exit;
}

// display $user info here
```

---

## Example: Display countries and cities with dynamic filtering and error handling

```php
<?php
try {
    $pdo = new PDO("mysql:host=localhost;dbname=world;charset=utf8", "root", "");
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    // Get country code from GET param
    $countryCode = $_GET['countryCode'] ?? null;

    if ($countryCode) {
        // Check if country exists
        $stmt = $pdo->prepare("SELECT Name FROM Country WHERE Code = ?");
        $stmt->execute([$countryCode]);
        $country = $stmt->fetchColumn();

        if (!$country) {
            header("Location: error.php");
            exit;
        }

        // Fetch cities for country
        $stmt = $pdo->prepare("SELECT Name FROM City WHERE CountryCode = ? ORDER BY Name");
        $stmt->execute([$countryCode]);
        $cities = $stmt->fetchAll(PDO::FETCH_COLUMN);

        if (count($cities) === 0) {
            echo "<p>No cities found for " . htmlspecialchars($country) . "</p>";
        } else {
            echo "<h2>Cities in " . htmlspecialchars($country) . "</h2><ul>";
            foreach ($cities as $city) {
                echo "<li>" . htmlspecialchars($city) . "</li>";
            }
            echo "</ul>";
        }
    } else {
        echo "<p>Please provide a countryCode in the URL, e.g. ?countryCode=USA</p>";
    }

} catch (PDOException $e) {
    die("DB Error: " . $e->getMessage());
}
```
