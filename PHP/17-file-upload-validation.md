
### 1. How to upload files using HTML forms and PHP using two approaches?

**Approach 1: Upload file and save it on the server**

* HTML form with `enctype="multipart/form-data"`:

```html
<form action="upload.php" method="POST" enctype="multipart/form-data">
  <input type="file" name="myfile" />
  <input type="submit" value="Upload" />
</form>
```

* PHP handles the upload and moves the file to a folder.

**Approach 2: Upload file and store file content in the database**

* Upload the file as above.
* In PHP, read file content and save it as BLOB in database.

---

### 2. Validating the uploaded file size, existence and extension using PHP.

In PHP, check:

* If file exists (uploaded)
* File size using `$_FILES['myfile']['size']`
* File extension using `pathinfo()`

Example:

```php
$allowed = ['jpg', 'png', 'pdf'];
$file = $_FILES['myfile'];

if ($file['error'] !== UPLOAD_ERR_OK) {
    die("Upload error");
}

$ext = strtolower(pathinfo($file['name'], PATHINFO_EXTENSION));
if (!in_array($ext, $allowed)) {
    die("Invalid file type");
}

if ($file['size'] > 2 * 1024 * 1024) { // 2MB max
    die("File too large");
}
```

---

### 3. Uploading files and storing them on the server with their original names using PHP.

```php
move_uploaded_file($_FILES['myfile']['tmp_name'], 'uploads/' . $_FILES['myfile']['name']);
```

Make sure `uploads/` folder is writable.

---

### 4. Uploading files and storing them on the server with hashed (encrypted) names using PHP.

Hash the filename to avoid collisions or security issues:

```php
$ext = pathinfo($_FILES['myfile']['name'], PATHINFO_EXTENSION);
$newName = md5(uniqid()) . '.' . $ext;
move_uploaded_file($_FILES['myfile']['tmp_name'], 'uploads/' . $newName);
```

---

### 5. Storing the uploaded files content in the database using PHP.

* Read file content:

```php
$content = file_get_contents($_FILES['myfile']['tmp_name']);
```

* Store `$content` in a BLOB column in the database using PDO.

---

### 6. Displaying the stored files from the server in PHP.

* Use `<img src="uploads/filename.jpg">` for images.
* For downloads: create a PHP script to read and output the file with headers.

---

### 7. Displaying the stored file from the database in PHP.

* Fetch the BLOB content from DB.
* Output it with proper headers:

```php
header("Content-Type: image/jpeg"); // or proper mime type
echo $file_content_from_db;
```

---

### 8. What is the usage of "pathinfo" function in PHP?

`pathinfo()` returns information about a file path such as directory, basename, extension, and filename.

Example:

```php
$info = pathinfo('uploads/file.jpg');
echo $info['extension']; // jpg
```

---

### 9. What is the usage of "move\_uploaded\_file" function in PHP?

Moves an uploaded file from temporary location to a new location safely.

---

### 10. What is the usage of "md5" function in PHP?

Generates an MD5 hash string (32 characters) of a given string. Used to hash filenames or passwords (though MD5 is weak for passwords).

---

### 11. What is data image and how to display it in HTML?

A data image is an image encoded as a Base64 string embedded directly in HTML:

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA..." />
```

---

### 12. What is the usage of "base64\_encode" function in PHP?

Encodes binary data (like image content) into a base64 string for embedding or transport.

---

### 13. What is the usage of "addslashes" function in PHP?

Adds backslashes before quotes (`'`, `"`) and backslash (`\`) to escape them, used for escaping strings before inserting into DB or other contexts.

---

## Example: Upload file, validate, store with hashed name, save content in DB, and display image inline

```php
<?php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    $file = $_FILES['myfile'];

    // Validate
    $allowed = ['jpg', 'jpeg', 'png', 'gif'];
    if ($file['error'] !== UPLOAD_ERR_OK) {
        die("Upload error");
    }
    $ext = strtolower(pathinfo($file['name'], PATHINFO_EXTENSION));
    if (!in_array($ext, $allowed)) {
        die("Invalid file type");
    }
    if ($file['size'] > 2 * 1024 * 1024) {
        die("File too large");
    }

    // Create hashed filename
    $newName = md5(uniqid()) . '.' . $ext;

    // Move file
    move_uploaded_file($file['tmp_name'], 'uploads/' . $newName);

    // Store content in DB (simplified, assuming PDO $pdo connection)
    $content = file_get_contents('uploads/' . $newName);
    $stmt = $pdo->prepare("INSERT INTO files (filename, content, mime) VALUES (?, ?, ?)");
    $stmt->execute([$newName, $content, mime_content_type('uploads/' . $newName)]);

    echo "File uploaded and saved!";
}

// To display stored image from DB:
$stmt = $pdo->query("SELECT content, mime FROM files WHERE id = 1");
$row = $stmt->fetch(PDO::FETCH_ASSOC);
if ($row) {
    $base64 = base64_encode($row['content']);
    echo '<img src="data:' . $row['mime'] . ';base64,' . $base64 . '" />';
}
```


