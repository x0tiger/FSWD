

### 1. How to handle AJAX requests using PHP?

AJAX sends requests to PHP scripts in the background without reloading the page. In PHP, you read request data (usually from `$_POST` or `$_GET`), process it, and return a response (usually JSON).

Example PHP (ajax-handler.php):

```php
header('Content-Type: application/json');

$data = $_POST['data'] ?? '';

$response = ['message' => "You sent: $data"];

echo json_encode($response);
```

JavaScript AJAX call:

```js
fetch('ajax-handler.php', {
  method: 'POST',
  headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
  body: 'data=Hello'
})
.then(res => res.json())
.then(data => console.log(data.message));
```

---

### 2. How to get data 20-by-20 from the database using AJAX and PHP?

Use **pagination** or **offset/limit** in SQL. The client sends the current page or offset, PHP queries with `LIMIT 20 OFFSET x`, then returns JSON data.

PHP example:

```php
$page = intval($_GET['page'] ?? 0);
$offset = $page * 20;

$stmt = $pdo->prepare("SELECT * FROM table LIMIT 20 OFFSET ?");
$stmt->execute([$offset]);
$rows = $stmt->fetchAll(PDO::FETCH_ASSOC);

echo json_encode($rows);
```

---

### 3. How to convert the content to JSON in PHP?

Use `json_encode()` function to convert PHP arrays or objects into JSON format string.

Example:

```php
$data = ['name' => 'Ali', 'age' => 25];
echo json_encode($data); // {"name":"Ali","age":25}
```

---

### 4. What is usage of "json\_encode" and "json\_decode" functions in PHP?

* `json_encode($data)` — converts PHP data into JSON string (for output or AJAX response).
* `json_decode($json, true)` — converts JSON string into PHP array/object (for processing incoming JSON).

Example:

```php
$json = '{"name":"Ali","age":25}';
$array = json_decode($json, true);
echo $array['name']; // Ali
```

---

### 5. How to use "Font Awesome" library in HTML?

Add Font Awesome CDN link in your `<head>`:

```html
<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet" />
```

Use icons like:

```html
<i class="fa fa-home"></i>
```

---

### 6. How to make animated icons using "Font Awesome"?

Add animation classes like `fa-spin` or `fa-pulse`:

```html
<i class="fa fa-spinner fa-spin"></i>
```

---

### 7. How to resize the icons using "Font Awesome"?

Use size classes:

```html
<i class="fa fa-home fa-2x"></i> <!-- 2 times bigger -->
<i class="fa fa-home fa-lg"></i>  <!-- large size -->
```

---

### 8. Why should we disable the buttons after pressing on them on AJAX calls?

To prevent multiple clicks or repeated requests which might cause duplicated actions or overload the server.

---

### 9. Why should we display loaders (spinners) after pressing on buttons that perform AJAX calls?

To give user feedback that action is in progress and improve user experience by showing the page is working, avoiding confusion.

---

## Example: Load user list 20-by-20 with AJAX and display loader and disable button during request

**HTML:**

```html
<button id="loadMore">Load More</button>
<div id="userList"></div>
<div id="loader" style="display:none;">Loading...</div>
```

**JavaScript:**

```js
let page = 0;
const btn = document.getElementById('loadMore');
const loader = document.getElementById('loader');
const userList = document.getElementById('userList');

btn.addEventListener('click', () => {
  btn.disabled = true;
  loader.style.display = 'block';

  fetch(`users.php?page=${page}`)
    .then(res => res.json())
    .then(users => {
      if (users.length === 0) {
        btn.textContent = 'No more users';
        btn.disabled = true;
      } else {
        users.forEach(u => {
          const div = document.createElement('div');
          div.textContent = u.name;
          userList.appendChild(div);
        });
        page++;
        btn.disabled = false;
      }
      loader.style.display = 'none';
    })
    .catch(() => {
      alert('Error loading users');
      btn.disabled = false;
      loader.style.display = 'none';
    });
});
```

**PHP (users.php):**

```php
<?php
header('Content-Type: application/json');
$page = intval($_GET['page'] ?? 0);
$offset = $page * 20;

$pdo = new PDO('mysql:host=localhost;dbname=mydb', 'user', 'pass');
$stmt = $pdo->prepare("SELECT name FROM users LIMIT 20 OFFSET ?");
$stmt->execute([$offset]);
$users = $stmt->fetchAll(PDO::FETCH_ASSOC);

echo json_encode($users);
```


