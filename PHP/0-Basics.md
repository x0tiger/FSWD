

###  **1. What is the big picture of web development?**

Web development is all about building websites and web apps. Think of it like this:

* **Frontend** → what users see: buttons, text, images.
* **Backend** → how things work behind the scenes: login, save data, etc.
* **Database** → where you store the data: like usernames, orders, messages.

So, when a user clicks a button:

1. The browser sends a request to the **server** (like Apache).
2. The **server** runs your **PHP code**.
3. It maybe talks to a **database**.
4. It sends back the result to the **browser**.

That’s the full cycle of web development.

---

###  **2. What is PHP?**

PHP is a **server-side language**, which means it runs on the server before anything goes to the browser.

You use PHP to:

* Handle form data.
* Connect to a database.
* Create login systems.
* Generate dynamic content.

PHP files end with `.php` and can also contain HTML.

---

###  **3. What is Apache?**

Apache is a **web server software**. It’s part of XAMPP. When someone opens your website in the browser, Apache is the one that handles that request and sends back the page.

If you’re using PHP locally, Apache is what makes it possible to run `.php` files in the browser.

---

###  **4. What is the extension of PHP files?**

PHP files always end with:

```
.php
```

Example:

```
index.php
```

This file can contain PHP, HTML, CSS, and JavaScript all in one.

---

###  **5. index.php vs. index.html**

* `index.html`: a static file. Only HTML. Can’t run PHP code.
* `index.php`: a dynamic file. You can run PHP code and include HTML, CSS, and JS too.

So if you need to use logic, or get data from a database, use `index.php`.

---

###  **6. Can PHP include HTML, CSS, and JavaScript?**

Yes. PHP can be mixed with HTML. And you can write CSS and JavaScript inside the HTML part.

#### Example:

```php
<!DOCTYPE html>
<html>
<head>
  <style>
    body { background-color: lightgrey; }
  </style>
</head>
<body>
  <h1><?php echo "Hello from PHP"; ?></h1>

  <script>
    console.log("Hello from JavaScript");
  </script>
</body>
</html>
```

---

###  **7. How to configure XAMPP to start your web application?**

Step-by-step:

1. Open **XAMPP Control Panel**.
2. Click **Start** next to **Apache** and **MySQL**.
3. Go to this folder on your PC:
   `C:\xampp\htdocs`
4. Paste your project folder inside `htdocs`.
5. In your browser, open:
   `http://localhost/your_project_name`

Now your PHP project will run in the browser.

---

###  **8. What are variables?**

Variables are names that store data. You can store text, numbers, etc.

They help you save values and use them later in your code.

---

###  **9. What are the primitive data types in PHP?**

* **String** → text
* **Integer** → whole numbers
* **Float** → decimal numbers
* **Boolean** → true or false
* **NULL** → no value

---

###  **10. How to declare variables in PHP?**

Use `$` before the name.

#### Example:

```php
$name = "Ali";
$age = 21;
$price = 99.99;
$is_online = true;
```

---

###  **11. What are constants?**

Constants are like variables, but the value doesn’t change.

---

###  **12. How to define constants in PHP?**

Use `define()` function.

#### Example:

```php
define("SITE_NAME", "MyWebsite");
echo SITE_NAME;
```

---

###  **13. How to display output in PHP?**

You can use:

* `echo` → simple and fast
* `print` → similar to echo
* `print_r` → for arrays
* `printf` → formatted output
* `sprintf` → formatted string (returns, doesn’t print)
* `var_dump` → debug info (type + value)

---

###  **14. Comparison: echo, print, print\_r, printf, sprintf, var\_dump**

| Function   | Purpose           | Example                         | Notes                   |
| ---------- | ----------------- | ------------------------------- | ----------------------- |
| `echo`     | Display text      | `echo "Hi";`                    | Most used               |
| `print`    | Display text      | `print "Hello";`                | Like echo               |
| `print_r`  | Print arrays      | `print_r($arr);`                | Good for testing arrays |
| `printf`   | Format + print    | `printf("Age: %d", 20);`        | Use placeholders        |
| `sprintf`  | Format + save     | `$x = sprintf("Hi %s", $name);` | Doesn’t print           |
| `var_dump` | Show value + type | `var_dump($x);`                 | Best for debugging      |

---

###  **15. What is string formatting in PHP?**

It’s a way to insert variables into a string in a clean way.

#### Example using `printf`:

```php
$name = "Nora";
$age = 30;
printf("Name: %s, Age: %d", $name, $age);
```

* `%s` = string
* `%d` = integer
* `%f` = float

You can control decimal places like this:

```php
$price = 49.999;
printf("Price: %.2f", $price); // Output: 49.99
```

