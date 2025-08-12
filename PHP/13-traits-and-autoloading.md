

### 1. What are traits in PHP?

Traits are a way to reuse methods across multiple classes without using inheritance. They let you horizontally reuse code in PHP.

---

### 2. How to use traits in PHP?

Define a trait with the `trait` keyword and use it inside a class with `use`.

```php
trait Logger {
    public function log($msg) {
        echo "Log: $msg";
    }
}

class User {
    use Logger;
}

$user = new User();
$user->log("User created");  // prints: Log: User created
```

---

### 3. What is the usage of "use" keyword in PHP?

* Inside classes, `use` imports traits.
* Outside classes, `use` imports namespaces.

---

### 4. What is the difference between static and non-static elements in PHP?

* **Static elements:** Belong to the class itself, not to objects. Accessed without creating an object.
* **Non-static elements:** Belong to objects (instances). You need to create an object to use them.

---

### 5. What is the usage of "static" keyword in PHP?

Declares properties or methods as static.

```php
class Test {
    public static $count = 0;
    
    public static function sayHi() {
        echo "Hi";
    }
}
```

---

### 6. How to use static elements inside and outside classes in PHP?

Inside class:

```php
self::$count++;
self::sayHi();
```

Outside class:

```php
Test::$count = 5;
Test::sayHi();
```

---

### 7. How to use non-static elements inside and outside classes in PHP?

Inside class, access using `$this`:

```php
$this->property;
$this->method();
```

Outside class, first create an object:

```php
$obj = new Test();
$obj->property;
$obj->method();
```

---

### 8. What is the difference between "require", "include", "require\_once" and "include\_once" in PHP?

* **require:** Includes a file; if file missing, script stops with fatal error.
* **include:** Includes a file; if missing, shows warning but script continues.
* **require\_once:** Same as require but includes file only once to avoid redeclaration.
* **include\_once:** Same as include but includes file only once.

---

### 9. What is serialization in PHP?

Serialization converts PHP data (like arrays or objects) into a string format that can be stored or transferred.

---

### 10. How to apply serialization in PHP?

Use `serialize()` to convert to string, and `unserialize()` to restore.

```php
$data = ['a' => 1, 'b' => 2];
$serialized = serialize($data);
$restored = unserialize($serialized);
```

---

### 11. What is the usage of "file\_put\_contents" and "file\_get\_contents" functions in PHP?

* `file_put_contents`: Write data to a file.
* `file_get_contents`: Read entire file contents as string.

```php
file_put_contents('test.txt', 'Hello world');
echo file_get_contents('test.txt');  // Outputs: Hello world
```

---

### 12. What is the usage of "serialize" and "unserialize" functions in PHP?

* `serialize`: Converts variable to storable string.
* `unserialize`: Converts string back to variable.

---

### 13. What is autoloading in PHP?

Autoloading automatically loads class files when a class is used without manual includes.

---

### 14. How to apply autoloading in PHP?

Register an autoloader function with `spl_autoload_register`.

```php
spl_autoload_register(function ($class) {
    include 'classes/' . $class . '.php';
});
```

---

### 15. How to check if a file exists or not in PHP?

Use `file_exists('filename')`, returns `true` or `false`.

---

### 16. What is the usage of "die" and "exit" functions in PHP?

Both stop the script immediately. You can pass a message.

```php
die("Fatal error");
exit("Goodbye");
```

---

## Example combining traits, static, serialization, and autoloading:

```php
<?php

trait Logger {
    public function log($msg) {
        echo "[LOG] $msg\n";
    }
}

class User {
    use Logger;

    public static $count = 0;
    public $name;

    public function __construct($name) {
        $this->name = $name;
        self::$count++;
        $this->log("User $name created.");
    }
}

// Autoloader example (assuming classes/User.php exists)
// spl_autoload_register(function($class) {
//     include "classes/$class.php";
// });

$user1 = new User("Ahmed");
$user2 = new User("Sara");

// Serialize user data
$data = serialize([$user1, $user2]);
file_put_contents("users.txt", $data);

// Read and unserialize
$usersFromFile = unserialize(file_get_contents("users.txt"));
foreach ($usersFromFile as $user) {
    $user->log("Loaded user: {$user->name}");
}

// Using static property
echo "Total users created: " . User::$count . "\n";

// Checking if file exists
if (!file_exists("config.php")) {
    die("Config file missing!");
}
```

