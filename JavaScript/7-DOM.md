

### 1. **What is the JavaScript DOM (Document Object Model)?**

The DOM is a programming interface for HTML and XML documents. It represents the **structure of the document** as a tree of nodes, where each node is an object representing a part of the page.

```html
<!-- HTML -->
<p>Hello <strong>World</strong></p>
```

This HTML is represented in the DOM as:

```
Document
 └── HTML
     └── BODY
         └── P
             ├── Text: "Hello"
             └── STRONG
                 └── Text: "World"
```

> 🟢 **DOM is used by JavaScript to access and manipulate web pages dynamically.**

---

### 2. **Types of DOM Nodes**

* **Document Node** – The root object (`document`)
* **Element Node** – HTML elements like `<div>`, `<p>`, `<a>`
* **Attribute Node** – Attributes like `href="..."`, `src="..."`
* **Text Node** – Text inside elements
* **Comment Node** – `<!-- comments -->`

```js
console.log(document.nodeType); // 9 => Document
console.log(document.body.nodeType); // 1 => Element
```

> 🔐 **DOM-based XSS often abuses Text Nodes or Attributes via innerHTML or setAttribute**

---

### 3. **Root,, Siblings and Children**

```html
<div id="parent">
  <p>First</p>
  <p>Second</p>
</div>
```

```js
const parent = document.getElementById('parent');
const firstChild = parent.children[0];
const sibling = firstChild.nextElementSibling;
```

* `parent` is the **root**
* `firstChild` and `sibling` are **siblings**
* Both `<p>` tags are **children** of `#parent`

---

### 4. **Mapping HTML to DOM**

Every element in HTML becomes a **node** in the DOM tree. JavaScript can traverse and manipulate these nodes using `document` object.

---

### 5. **How to Access the DOM**

You use the global `document` object.

```js
document.getElementById("myId")
document.querySelector(".myClass")
```

---

### 6. **Common document properties**

```js
document.head
document.body
document.title = "New Title";
document.images
document.forms
document.body.firstElementChild
```

```js
const elem = document.getElementById("myDiv");
elem.classList.add("highlight");
elem.style.color = "blue";
```

---

### 7. **Common DOM Methods**

#### Select Elements

```js
document.getElementById("id")
document.getElementsByClassName("class")
document.querySelector("div.container")
document.querySelectorAll("p")
```

#### Modify Elements

```js
let el = document.getElementById("demo");
el.innerText = "Safe Text"; // Text only
el.innerHTML = "<b>Dangerous if user input</b>"; // Can lead to XSS
```

> ⚠️ **Never insert untrusted data via innerHTML → Can cause DOM XSS!**

#### Attributes

```js
el.setAttribute("title", "Hello");
let attr = el.getAttribute("title");
```

#### Create & Append Elements

```js
let newP = document.createElement("p");
newP.textContent = "This is new";
document.body.appendChild(newP);
```

---

### 8. **Style and Class Manipulation**

```js
el.style.color = "red";
el.classList.add("active");
el.classList.remove("hidden");
el.classList.contains("btn");
```

---

### 9. **Events and Handlers**

#### Create Events

```js
button.onclick = function() {
  alert("Clicked!");
};
```

#### Add Listeners

```js
button.addEventListener("click", function() {
  console.log("Button clicked");
});
```

🔐 **DOM XSS Example:**

```js
// Bad practice - vulnerable to DOM XSS
let userInput = location.hash.substring(1); // URL: site.com#<script>alert(1)</script>
document.getElementById("output").innerHTML = userInput;
```

✅ **Safe approach:**

```js
document.getElementById("output").innerText = userInput;
```

---

### 10. **Insert Positions**

```js
el.insertAdjacentHTML("beforebegin", "<p>Before</p>");
el.insertAdjacentHTML("afterend", "<p>After</p>");
el.insertAdjacentHTML("afterbegin", "<p>Top inside</p>");
el.insertAdjacentHTML("beforeend", "<p>Bottom inside</p>");
```

---

### 11. **Inserting vs Concatenating**

* **Inserting to DOM** uses functions like `appendChild`, `insertAdjacentHTML`.
* **Concatenation** is string-based and often misused with `innerHTML`, risking XSS.

---

### 🟢 Summary in Arabic 

* **DOM** هو تمثيل شجري لصفحة HTML.
* تقدر توصل لأي عنصر أو تعدله باستخدام `document`.
* **innerHTML** خطير لو دخلت فيه بيانات من المستخدم.
* استخدم `textContent` أو `innerText` لتجنب XSS.
* **أنواع العقد**: المستند، العنصر، النص، التعليق.
* **DOM XSS** بيحصل لما تعرض بيانات غير موثوقة على الصفحة بدون فحص.
