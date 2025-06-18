## 1. What is Object-Oriented JavaScript and Prototyping?

**Object-Oriented Programming (OOP)** is a programming model that organizes code into reusable components called "objects". These objects contain:

- **Properties** (data),
    
- **Methods** (functions that act on the data),
    
- And they can inherit from other objects.
    

In JavaScript, OOP is based on a **prototype-based inheritance** system.

Each object in JavaScript has an internal link to another object called a **prototype**. If a property or method is not found in the object itself, JavaScript looks for it in its prototype.

This is different from class-based inheritance in languages like Java or C++; JavaScript uses **prototypal inheritance**.

---

## 2. Simple Comparison Between ES5 and ES6

|Feature|ES5|ES6 (ES2015)|
|---|---|---|
|Variable declaration|`var`|`let`, `const`|
|Functions|Regular functions (`function`)|Arrow functions (`() => {}`)|
|Classes|Constructor functions|`class`, `constructor()`|
|Inheritance|Manual prototype chaining|`extends`, `super()`|
|Modules|Not supported|`import`, `export`|
|Strings|Concatenation with `+`|Template literals `` `Hi ${}` ``|

**Summary:**

- ES6 introduces `class` syntax to make object-oriented programming easier.
    
- Internally, classes in ES6 still use prototypes — it's just cleaner syntax.
    

---

## 3. What is a Prototype?

A **prototype** is an object that other objects can inherit from.

Every JavaScript object has a hidden internal property `[[Prototype]]`, which is usually accessible using the `__proto__` property or via `Object.getPrototypeOf(obj)`.

If a property or method doesn't exist directly on the object, JavaScript looks for it in its prototype.

---

## 4. How to Create a Prototype?

Usually, a prototype is created when you define a constructor function and then assign methods to its prototype.

Example:

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = function() {
  console.log("Hello, my name is " + this.name);
};
```

Now any object created using `Person` will inherit `sayHello()`.

---

## 5. How to Create a Function Constructor?

A **constructor function** is a regular function used with the `new` keyword to create objects.

Example:

```javascript
function Car(model, year) {
  this.model = model;
  this.year = year;
}

let car1 = new Car("Toyota", 2022);
```

When used with `new`:

1. A new empty object is created.
    
2. `this` is bound to the new object.
    
3. The prototype is linked.
    
4. The constructor runs and returns the object.
    

---

## 6. What is `this` Inside a Function?

`this` refers to the object that the function is being executed on.

- In a constructor: `this` refers to the newly created object.
    
- In a method: `this` refers to the object calling the method.
    
- In global functions: `this` refers to the global object (`window` in browsers), unless in `strict` mode.
    

Example:

```javascript
function User(name) {
  this.name = name;
  console.log(this); // logs the new object created by new User()
}
```

---

## 7. How to Create an Object from a Prototype?

Two common ways:

**Using constructor:**

```javascript
let user1 = new Person("Ali");
```

**Using Object.create():**

```javascript
let newUser = Object.create(Person.prototype);
newUser.name = "Sara";
```

In both cases, `newUser` inherits from `Person.prototype`.

---

## 8. How to Add Properties and Methods to a Prototype?

You can add shared functionality like this:

```javascript
Car.prototype.getInfo = function() {
  return this.model + " (" + this.year + ")";
};
```

All objects created using `Car` will have access to `getInfo()`, without duplicating the function for each object.

This saves memory and improves consistency.

---

## 9. What is Prototype Chaining?

When JavaScript can't find a property or method in the object itself, it continues looking up the **prototype chain**:

1. Starts with the object itself.
    
2. Moves to its prototype.
    
3. Then the prototype’s prototype.
    
4. ...until it reaches `null`.
    

This lookup process is called **prototype chaining**.

Example:

```javascript
let obj = {};
obj.toString(); // found in Object.prototype
```

---

## 10. How Does JavaScript Find a Property or Method?

The JavaScript engine follows this process:

1. Check if the property exists on the object.
    
2. If not found, go to its prototype.
    
3. Repeat until found or the end of the chain (`null`).
    

Example:

```javascript
let car = new Car("BMW", 2023);
console.log(car.toString()); // not in car, found in Object.prototype
```

---

## 11. How to Apply Prototype Chaining?

Let’s look at a full example:

```javascript
function Animal() {}
Animal.prototype.eat = function() {
  console.log("Eating...");
};

function Dog(name) {
  this.name = name;
}

// Make Dog inherit from Animal
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

let myDog = new Dog("Max");
myDog.eat(); // Inherited from Animal
```

**Explanation:**

- `Dog` does not have an `eat` method.
    
- JS looks in `Dog.prototype`, doesn't find it.
    
- Then goes to `Animal.prototype`, finds it there.
    
- This is prototype chaining in action.
