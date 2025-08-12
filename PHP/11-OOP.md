

### 1. What is a class and object in programming?

* **Class:** A blueprint or template to create objects. It defines properties (variables) and methods (functions).
* **Object:** An instance of a class. It holds actual data and can use class methods.

Example:

```php
class Car {
    public $color;
}

$myCar = new Car();  // $myCar is an object of class Car
$myCar->color = "red";
```

---

### 2. What is object-oriented programming (OOP)?

A programming paradigm based on **objects** that combine data and behavior. OOP helps organize code into reusable and modular components.

---

### 3. What is the advantage of classes over functions?

* Classes bundle data and functions together.
* Allow creating multiple instances (objects) with different states.
* Support concepts like inheritance, encapsulation, and polymorphism which functions alone can’t handle easily.

---

### 4. What are the different concepts of OOP?

* **Abstraction**: Hiding complex details, showing only essential features.
* **Encapsulation**: Keeping data safe by restricting access using access modifiers.
* **Inheritance**: One class inherits properties and methods from another.
* **Polymorphism**: Same function/method name works differently based on context.
* **Overloading**: Ability to define multiple methods with the same name but different parameters (PHP supports limited forms).
* **Overriding**: Subclass provides a specific implementation of a method from its parent class.

---

### 5. What is abstraction, polymorphism, overloading, overriding, encapsulation and inheritance in OOP?

* **Abstraction:** Focus on what an object does, not how it does it.
* **Polymorphism:** Same interface, different implementation.
* **Overloading:** Same method name, different parameters (PHP doesn’t support method overloading like Java but can mimic it).
* **Overriding:** Subclass redefines a parent method.
* **Encapsulation:** Protecting data using private/protected modifiers.
* **Inheritance:** Child class inherits from parent class.

---

### 6. How to write a class in PHP?

```php
class Person {
    public $name;

    public function sayHello() {
        return "Hello, " . $this->name;
    }
}
```

---

### 7. What are the different access modifiers and their usages?

* **public:** Accessible everywhere.
* **private:** Accessible only inside the class.
* **protected:** Accessible inside class and subclasses.

---

### 8. How to create a new object from a class in PHP?

```php
$person = new Person();
```

---

### 9. How to access members or functions from an object in PHP?

```php
$person->name = "Ahmed";
echo $person->sayHello();
```

---

### 10. How to access non-static members (variables) inside the class in PHP?

Use `$this->memberName` inside class methods.

---

### 11. What is usage of `this` keyword inside a class in PHP?

It refers to the current object instance, allowing access to its properties and methods.

---

### 12. How to write expressions inside double quotes in PHP?

Use curly braces `{}` around variables for complex expressions.

```php
echo "Hello, {$this->name}";
```

---

### 13. What is constructors and destructors in PHP classes?

* **Constructor:** A method called automatically when an object is created, usually named `__construct`.
* **Destructor:** A method called automatically when an object is destroyed, usually named `__destruct`.

---

### 14. How to pass values to the class constructor in PHP?

```php
class Person {
    public $name;
    public function __construct($name) {
        $this->name = $name;
    }
}

$person = new Person("Ahmed");
```

---

### 15. What is the usage of `__toString` class function in PHP?

It defines how an object converts to a string.

```php
class Person {
    public $name;
    public function __toString() {
        return $this->name;
    }
}
```

---

### 16. How to convert an object to an array in PHP?

Use `(array)` cast or `get_object_vars()`.

```php
$arr = (array)$person;
```

---

### 17. How to convert an object to a string in PHP?

Use `__toString` method or serialize it.

---

### 18. What is explicit casting in PHP?

Manually converting a value from one type to another, e.g., `(int)$var`, `(string)$var`.

---

### 19. How to convert an array to an object in PHP?

Cast array to object:

```php
$obj = (object)$array;
```

---

## Example — OOP 

```php
<?php

class User {
    private $name;
    protected $email;
    public $role;

    public function __construct($name, $email, $role = "user") {
        $this->name = $name;
        $this->email = $email;
        $this->role = $role;
    }

    public function getName() {
        return $this->name;
    }

    public function __toString() {
        return "User: {$this->name}, Email: {$this->email}, Role: {$this->role}";
    }
}

class Admin extends User {
    public function getRole() {
        return strtoupper($this->role);
    }

    // Overriding getName method
    public function getName() {
        return "Admin: " . parent::getName();
    }
}

$user = new User("Ali", "ali@example.com");
$admin = new Admin("Sara", "sara@example.com", "admin");

echo $user->getName();  // Ali
echo "\n";
echo $admin->getName(); // Admin: Sara
echo "\n";
echo $admin->getRole(); // ADMIN
echo "\n";

// Convert object to array
print_r((array)$admin);

// Convert array to object
$arr = ['name' => 'John', 'email' => 'john@example.com'];
$obj = (object)$arr;
echo $obj->name; // John
```

