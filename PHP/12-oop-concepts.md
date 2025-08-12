

### 1. What is inheritance?

Inheritance is a feature in OOP where a class (child/subclass) inherits properties and methods from another class (parent/superclass). This helps reuse code and create a hierarchy of classes.

---

### 2. What are the advantages of inheritance?

* Code reuse: Child classes can use code from parent classes.
* Easy maintenance: Changes in the parent class propagate to children.
* Logical hierarchy: Models real-world relationships.
* Extensibility: Add new features without modifying existing code.

---

### 3. How to apply inheritance in PHP?

Use the `extends` keyword.

```php
class ParentClass {
    public function sayHello() {
        echo "Hello from Parent";
    }
}

class ChildClass extends ParentClass {
    // inherits sayHello() method
}
```

---

### 4. How to execute the constructor of the parent class in PHP?

Inside the child class constructor, call `parent::__construct()`.

```php
class ParentClass {
    public function __construct() {
        echo "Parent constructor\n";
    }
}

class ChildClass extends ParentClass {
    public function __construct() {
        parent::__construct(); // call parent's constructor
        echo "Child constructor\n";
    }
}
```

---

### 5. What is overriding?

Overriding is when a child class redefines a method that exists in the parent class, providing a new implementation.

---

### 6. How is overriding applied in PHP?

Simply declare the method with the same name in the child class.

```php
class ParentClass {
    public function greet() {
        echo "Hello from Parent";
    }
}

class ChildClass extends ParentClass {
    public function greet() {
        echo "Hello from Child";
    }
}
```

---

### 7. What is overloading?

In PHP OOP, **overloading** refers to dynamically creating properties or methods at runtime using magic methods like `__get()`, `__set()`, `__call()`, etc. It’s different from traditional method overloading in some other languages.

---

### 8. What is encapsulation?

Encapsulation means hiding the internal state (variables) of an object and requiring all interaction to be performed through methods, using access modifiers (`private`, `protected`, `public`).

---

### 9. What is abstraction?

Abstraction means hiding complex implementation details and showing only essential features to the user. In PHP, it is done by defining abstract classes and methods.

---

### 10. How to apply abstraction in PHP?

Use `abstract` keyword on classes and methods.

```php
abstract class Animal {
    abstract public function makeSound();

    public function sleep() {
        echo "Sleeping";
    }
}

class Dog extends Animal {
    public function makeSound() {
        echo "Bark";
    }
}
```

---

### 11. What is the usage of "final", "abstract" and "extends" keywords in PHP?

* **final:**

  * Used to prevent class inheritance (`final class ClassName {}`) or method overriding (`final function methodName() {}`).
* **abstract:**

  * Used to declare abstract classes or methods that must be implemented by subclasses.
* **extends:**

  * Used to inherit a class (inheritance).

---

##  Example demonstrating inheritance, overriding, abstraction, encapsulation, and final:

```php
<?php

abstract class Vehicle {
    protected $speed;

    public function __construct($speed = 0) {
        $this->speed = $speed;
    }

    abstract public function move();

    public function getSpeed() {
        return $this->speed;
    }
}

class Car extends Vehicle {
    private $brand;

    public function __construct($brand, $speed) {
        parent::__construct($speed);
        $this->brand = $brand;
    }

    public function move() {
        echo "{$this->brand} car is moving at {$this->speed} km/h\n";
    }

    // Overriding getSpeed method
    public function getSpeed() {
        return "Current speed: " . parent::getSpeed() . " km/h";
    }
}

final class Bike extends Vehicle {
    public function move() {
        echo "Bike is moving at {$this->speed} km/h\n";
    }
}

// Cannot extend Bike because it is final
// class MountainBike extends Bike {}

$car = new Car("Toyota", 100);
$car->move();
echo $car->getSpeed() . "\n";

$bike = new Bike(50);
$bike->move();
```


