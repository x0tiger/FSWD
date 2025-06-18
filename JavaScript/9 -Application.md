

##  What You'll Learn:

1. How to **add/remove posts** dynamically using JavaScript and prototyping
    
2. How to **remove only the selected post**
    
3. Use of **`split()`** function
    
4. Use of **`remove()`** to delete an element from the DOM
    
5. Use of **`confirm()`** to ask the user before deleting
    

---

##  Final Output

- A form to add a post (title + body)
    
- Posts displayed in Bootstrap cards
    
- Each post has a delete button
    
- Delete confirmation before removing the post
    

---

##  HTML Structure (with Bootstrap 4)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Post Manager</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body class="p-4">

  <div class="container">
    <h2 class="mb-4">Add Post</h2>
    <form id="postForm">
      <div class="form-group">
        <input type="text" class="form-control" id="title" placeholder="Enter Title">
      </div>
      <div class="form-group">
        <textarea class="form-control" id="body" placeholder="Enter Body"></textarea>
      </div>
      <button type="submit" class="btn btn-primary">Add Post</button>
    </form>

    <hr>

    <h3>Posts</h3>
    <div id="postsContainer"></div>
  </div>

  <script src="app.js"></script>
</body>
</html>
```

---

##  JavaScript (with Prototyping) – `app.js`

```javascript
// Constructor for a Post
function Post(title, body) {
  this.title = title;
  this.body = body;
}

// Prototype to render post
Post.prototype.render = function() {
  const container = document.getElementById("postsContainer");

  const card = document.createElement("div");
  card.className = "card mt-3";

  card.innerHTML = `
    <div class="card-body">
      <h5 class="card-title">${this.title}</h5>
      <p class="card-text">${this.body}</p>
      <button class="btn btn-danger btn-sm delete-post">Delete</button>
    </div>
  `;

  container.appendChild(card);
};

// Handle form submission
document.getElementById("postForm").addEventListener("submit", function(e) {
  e.preventDefault();

  const title = document.getElementById("title").value.trim();
  const body = document.getElementById("body").value.trim();

  if (!title || !body) {
    alert("Please fill in both fields.");
    return;
  }

  const newPost = new Post(title, body);
  newPost.render();

  // Reset form
  this.reset();
});

// Remove selected post
document.getElementById("postsContainer").addEventListener("click", function(e) {
  if (e.target.classList.contains("delete-post")) {
    if (confirm("Are you sure you want to delete this post?")) {
      e.target.closest(".card").remove();
    }
  }
});
```

---

##  Explanation of the Key Concepts:

###  1. How to remove **only** the selected element?

We use:

```javascript
e.target.closest(".card").remove();
```

This removes **only the card** that contains the clicked delete button. It does **not** affect other posts.

---

###  2. What is the usage of `split()` function?

The `split()` function is used to divide a string into an array, based on a delimiter.

Example:

```javascript
let fullName = "Elhussieny Elnemr";
let parts = fullName.split(" "); // ["Elhussieny", "Elnemr"]
```

---

### 3. How to remove an element from the DOM?

Using the `remove()` method:

```javascript
element.remove();
```

This deletes the element entirely from the DOM.

---

###  4. How to confirm before deleting?

Using the `confirm()` function:

```javascript
if (confirm("Are you sure?")) {
  // Delete
}
```

- `confirm()` returns `true` if the user clicks "OK", and `false` if "Cancel" is clicked.
    
- This is perfect to **avoid accidental deletion**.
    

---

##  Summary

- We created a **post manager** using **Bootstrap 4 + JavaScript prototypes**
    
- You learned how to:
    
    - Add elements to the DOM
        
    - Remove only selected elements
        
    - Use `confirm()`, `remove()`, and `split()`
        
- The code is modular and beginner-friendly
    

---

