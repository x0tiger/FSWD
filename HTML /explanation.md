
##  What is HTML?

**HTML (HyperText Markup Language)** is the standard language used to create and structure content on the web.  
It tells the browser how to display text, images, links, and other elements.


##  How to Create an HTML File?

1. Open any text editor (e.g., VS Code, Notepad, Sublime Text).
    
2. Save the file with a `.html` extension — for example: `index.html`.
    
3. Open the file in a web browser to view the result.
    

---

##  Default Structure of an HTML Webpage :)

```
<!DOCTYPE html>
<html>
  <head>
    <title>My First Page</title>
  </head>
  <body>
    <h1>Hello, world!</h1>
  </body>
</html>
```

---

##  What are Elements, Tags, and Attributes?

- **Element**: The complete structure, including tags and content.  
    Example: `<p>Hello</p>`
    
- **Tags**: The start and end markers of an element.  
    Example: `<p>` is the opening tag, `</p>` is the closing tag.
    
- **Attributes**: Extra information added inside the opening tag.  
    Example: `<img src="image.jpg" alt="A picture">`
    

---

##  Self-Closing Tags vs Open-Close Tags

|Type|Example|Description|
|---|---|---|
|Self-Closing|`<img />`, `<br />`|No content inside, ends itself|
|Open-Close|`<p>Text</p>`|Has opening and closing tags|

---

##  Block-level Elements vs Inline-level Elements

|   |   |   |
|---|---|---|
|Type|Examples|Behavior|
|Block-level|`<div>`, `<p>`, `<h1>`|Starts on a new line, takes full width|
|Inline-level|`<span>`, `<b>`, `<a>`|Stays in line, takes only needed width|

---

##  What are Meta Tags?

**Meta tags** provide metadata (information about the webpage) to the browser and search engines.

Example:

```
<meta charset="UTF-8">
<meta name="description" content="A cool website">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

They go inside the `<head>` section.

---

##  Key-Value Attributes vs Boolean Attributes

|           |                                    |                                  |
| --------- | ---------------------------------- | -------------------------------- |
| Type      | Example                            | Description                      |
| Key-Value | `<img src="image.jpg" alt="desc">` | Always includes key and value    |
| Boolean   | `<input type="checkbox" checked>`  | Can appear with or without value |

> Boolean attributes like `checked`, `disabled`, and `required` are either present or not — no need for a value.

---

##  Common Tags: `p`, `u`, `b`, `s`, `i`

|       |                    |                               |
| ----- | ------------------ | ----------------------------- |
| Tag   | Meaning            | Example                       |
| `<p>` | Paragraph          | `<p>This is a paragraph.</p>` |
| `<u>` | Underlined text    | `<u>Underlined</u>`           |
| `<b>` | Bold text          | `<b>Bold</b>`                 |
| `<s>` | Strikethrough text | `<s>Old Price</s>`            |
| `<i>` | Italic text        | `<i>Italic</i>`               |

---
##  HTML Tags: `p`, `blockquote`, `pre`, `br`, `hr`, `sup`, `sub`

|Tag|Description|Example|
|---|---|---|
|`<p>`|Paragraph of text|`<p>Hello World!</p>`|
|`<blockquote>`|Quoted block (usually indented)|`<blockquote>This is a quote</blockquote>`|
|`<pre>`|Preserves whitespace and formatting (preformatted text)|`<pre> Code block </pre>`|
|`<br>`|Line break (self-closing)|`Line 1<br>Line 2`|
|`<hr>`|Horizontal line (self-closing)|`<hr>`|
|`<sup>`|Superscript (above text line)|`x<sup>2</sup>` → x²|
|`<sub>`|Subscript (below text line)|`H<sub>2</sub>O` → H₂O|

---

##  What is Ignored by HTML?

- **Extra whitespace** (spaces, tabs, newlines) is **collapsed** into a single space.
    
- **Comments** are ignored:
    
    ```
    <!-- This is a comment -->
    ```
    
- Unknown or deprecated tags are ignored or not rendered properly.
    

---

##  What Are Lists?

**Lists** allow you to group related content in a structured way.

###  Types of Lists:

1. **Ordered List** (numbered):
    
    ```
    <ol>
      <li>First</li>
      <li>Second</li>
    </ol>
    ```
    
2. **Unordered List** (bulleted):
    
    ```
    <ul>
      <li>Apple</li>
      <li>Banana</li>
    </ul>
    ```
    
3. **Definition List** (terms and descriptions):
    
    ```
    <dl>
      <dt>HTML</dt>
      <dd>HyperText Markup Language</dd>
    </dl>
    ```
    

---

##  Nested HTML Lists

Lists inside lists (multilevel structure):

```
<ul>
  <li>Fruits
    <ul>
      <li>Apple</li>
      <li>Banana</li>
    </ul>
  </li>
</ul>
```

---

##  List Attributes: `start`, `type`, `reversed`

Used with `<ol>` to control the list behavior.

|   |   |   |
|---|---|---|
|Attribute|Description|Example|
|`start`|Starts the list from a specific number|`<ol start="5">` → starts from 5|
|`type`|Changes marker style (1, A, a, I, i)|`<ol type="A">` → A, B, C…|
|`reversed`|Reverses the order of the list|`<ol reversed>`|

---

##  What Are HTML Entities?

Used to display reserved or special characters in HTML.

|   |   |   |
|---|---|---|
|Entity|Displays|Description|
|`&lt;`|`<`|Less than symbol|
|`&gt;`|`>`|Greater than symbol|
|`&amp;`|`&`|Ampersand|
|`&quot;`|`"`|Double quote|
|`&nbsp;`|(space)|Non-breaking space|

---

##  HTML Headings: `h1` to `h6`

Used to define titles or headings on the page.

|        |          |                          |
| ------ | -------- | ------------------------ |
| Tag    | Size     | Example                  |
| `<h1>` | Largest  | `<h1>Main Title</h1>`    |
| `<h2>` | Smaller  | `<h2>Section Title</h2>` |
| `<h3>` | ...      | `<h3>Subsection</h3>`    |
| `<h4>` | ...      | `<h4>Minor Heading</h4>` |
| `<h5>` | ...      | `<h5>Note</h5>`          |
| `<h6>` | Smallest | `<h6>Fine Print</h6>`    |

> **Only one** `**<h1>**` should be used per page for SEO and accessibility.

--------------------------------------------------------------
##  ID vs. Class Attributes

|Attribute|ID|Class|
|---|---|---|
|**Usage**|Identifies a **unique element** in the document.|Assigns **one or more elements** to a group for styling or JS.|
|**Uniqueness**|Must be unique within the page (only one element can have the same ID).|Can be used for multiple elements on the page.|
|**CSS/JS Targeting**|Can be targeted with `#id` in CSS/JS.|Can be targeted with `.class` in CSS/JS.|

### Example:

```
<div id="header">This is the header</div>
<p class="important">This is an important paragraph</p>
```

---

##  `div` vs. `span` Tags

|   |   |   |
|---|---|---|
|Tag|`div`|`span`|
|**Type**|Block-level element.|Inline-level element.|
|**Purpose**|Groups elements together (useful for layout).|Groups inline elements or text.|
|**Usage**|`<div>` is used to structure the layout (larger containers).|`<span>` is used for styling smaller parts of text or inline elements.|

### Example:

```
<div> <!-- Block element for grouping content -->
  <p>This is a paragraph in a div.</p>
</div>

<span>Highlighted text</span> <!-- Inline element for small grouping -->
```

---

##  What Are Links? Using Anchor Tags (`<a>`)

**Links** are created using the `<a>` (anchor) tag. It allows users to navigate to different pages, sections, or external resources.

### Basic Example:

```
<a href="https://example.com">Visit Example</a>
```

- `**href**`: Specifies the destination URL.
    

---

##  Relative vs. Absolute Linking

|   |   |   |
|---|---|---|
|Type|Example|Description|
|**Relative**|`<a href="/about.html">About Us</a>`|Links to a file relative to the current directory.|
|**Absolute**|`<a href="https://example.com">Example</a>`|Full URL that points to a specific website or resource.|

---

##  Targeting an Element in the Same Webpage

To create a **link** that targets an **element on the same page**:

1. Add an **ID** to the target element.
    
2. Use a **hash (**`**#**`**)** in the `href` attribute to link to that ID.
    

### Example:

```
<a href="#section2">Go to Section 2</a>

<!-- Later in the page -->
<h2 id="section2">This is Section 2</h2>
```

---

##  Blank, Named, and Self Targets in the Anchor Tag

|   |   |   |
|---|---|---|
|Target Attribute|Description|Example|
|`**_blank**`|Opens the link in a new tab or window.|`<a href="https://example.com" target="_blank">Visit</a>`|
|`**_self**`|Default behavior, opens the link in the same window/tab.|`<a href="https://example.com" target="_self">Visit</a>`|
|`**_parent**`|Opens the link in the parent frame (if using frames).|`<a href="https://example.com" target="_parent">Visit</a>`|
|`**_top**`|Opens the link in the full window.|`<a href="https://example.com" target="_top">Visit</a>`|
|**Named Target**|Opens the link in a window or frame with a specific name.|`<a href="https://example.com" target="myWindow">Visit</a>`|

---

##  How to Link an Image? Using Image Tags (`<img>`)

To **link an image** to a webpage or resource, use the `<img>` tag with the `src` attribute for the image path and the `alt` attribute for alternative text.

### Example:

```
<a href="https://example.com">
  <img src="image.jpg" alt="Description of the image" />
</a>
```

- The image becomes a clickable link to `https://example.com`.
    

---

##  Using Other Protocols (e.g., "mailto")

You can use the `mailto` protocol to create a **link** that opens the user's default email client to send an email.

### Example:

```
<a href="mailto:someone@example.com">Send Email</a>
```

- Clicking this link will open the user's email client with a new email addressed to `someone@example.com`.
    

--------------------------------------
##  Using `<video>` and `<audio>` Tags

### **Video Tag (**`**<video>**`**)**

The `<video>` tag is used to embed video files on a webpage. You can also control playback, volume, and other features with attributes.

#### Example:

```
<video width="600" controls>
  <source src="movie.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
```

- `**controls**`: Adds playback controls (play, pause, volume).
    
- `**width**`: Specifies the width of the video.
    
- `**source**`: Specifies the video file and its format.
    

### **Audio Tag (**`**<audio>**`**)**

The `<audio>` tag is used for embedding audio files, like music or sound effects, with playback controls.

#### Example:

```
<audio controls>
  <source src="audio.mp3" type="audio/mp3">
  Your browser does not support the audio element.
</audio>
```

- `**controls**`: Adds audio controls like play, pause, volume.
    
- `**source**`: Specifies the audio file and format.
    

---

##  Using `<iframe>` Tag and Embedding from YouTube and SoundCloud

The `<iframe>` tag is used to embed external content like videos, maps, and social media posts.

### **Embedding YouTube Video:**

To embed a YouTube video, get the embed link from the YouTube share option.

#### Example:

```
<iframe width="560" height="315" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
```

- `**src**`: Contains the URL of the YouTube video.
    
- `**width**` **/** `**height**`: Specifies the size of the embedded video.
    

### **Embedding SoundCloud Track:**

To embed a SoundCloud track, use the embed code provided by SoundCloud.

#### Example:

```
<iframe width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/123456789&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false"></iframe>
```

- `**src**`: Contains the SoundCloud track URL.
    

---

##  Creating Tables in HTML

The `<table>` tag is used to create a table in HTML. Inside the table, you use `<tr>` for rows, `<th>` for header cells, and `<td>` for regular cells.

### Example:

```
<table border="1">
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Alice</td>
    <td>30</td>
  </tr>
  <tr>
    <td>Bob</td>
    <td>25</td>
  </tr>
</table>
```

- `**border**`: Adds a border around the table.
    
- `**<th>**`: Represents a header cell.
    
- `**<td>**`: Represents a regular table cell.
    

---

##  Applying `rowspan` and `colspan` Attributes

- `**rowspan**`: Allows a cell to span across multiple rows.
    
- `**colspan**`: Allows a cell to span across multiple columns.
    

### Example:

```
<table border="1">
  <tr>
    <th rowspan="2">Name</th>
    <th colspan="2">Contact Info</th>
  </tr>
  <tr>
    <td>Phone</td>
    <td>Email</td>
  </tr>
  <tr>
    <td>Alice</td>
    <td>123-4567</td>
    <td>alice@example.com</td>
  </tr>
</table>
```

- In this example, the `**Name**` header spans 2 rows, and the `**Contact Info**` header spans 2 columns.

---
##  GET vs. POST HTTP Methods

|Feature|**GET**|**POST**|
|---|---|---|
|**Purpose**|Retrieve data from the server|Submit data to the server|
|**Data in URL?**|Yes (sent via URL parameters)|No (sent in the request body)|
|**Security**|Less secure (data visible in URL)|More secure for sensitive data|
|**Caching**|Can be cached|Not cached|
|**Use Cases**|Search queries, page loads|Login forms, submitting data|

---

##  Using Forms in HTML

The `<form>` tag is used to collect user input and send it to a server.

### Example:

```
<form action="/submit" method="POST">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" required>
  <button type="submit">Submit</button>
</form>
```

- `**action**`: URL where form data will be sent.
    
- `**method**`: HTTP method (`GET` or `POST`).
    

---

##  Form Tags: `label`, `input`, `select`, `option`, `fieldset`, `legend`, `datalist`

###  `<label>`

Defines a label for an input element.

```
<label for="email">Email:</label>
<input type="email" id="email" name="email">
```

###  `<input>`

Used for various types of user input.

```
<input type="text" name="username">
```

###  `<select>` and `<option>`

Creates a dropdown menu.

```
<select name="country">
  <option value="us">United States</option>
  <option value="uk">United Kingdom</option>
</select>
```

###  `<fieldset>` and `<legend>`

Groups related form elements.

```
<fieldset>
  <legend>Personal Info</legend>
  <input type="text" name="name">
</fieldset>
```

###  `<datalist>`

Provides autocomplete options.

```
<input list="browsers" name="browser">
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
</datalist>
```

---

##  Common Attributes

|   |   |
|---|---|
|Attribute|Description|
|`maxlength`|Maximum number of characters allowed|
|`minlength`|Minimum number of characters required|
|`required`|Makes the field mandatory|
|`min`|Minimum value (for number/date inputs)|
|`max`|Maximum value (for number/date inputs)|
|`placeholder`|Hint text inside the input box|
|`value`|Default or preset value|
|`type`|Type of input (`text`, `email`, `number`, etc.)|
|`name`|Key name used when sending form data|

---

##  What is Validation?

**Validation** is the process of checking if the user's input meets the required criteria **before** submitting the form.

###  Why Perform Validation?

- Prevent invalid or incomplete data.
    
- Enhance user experience with immediate feedback.
    
- Reduce errors on the backend.
    
- Improve security (e.g., block malicious inputs).
    

There are **two types** of validation:

- **Client-side**: Performed in the browser (HTML5 or JavaScript).
    
- **Server-side**: Performed on the server after submission (more secure).
    

---
## Design Login and registration page

###  `login.html`

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Login</title>
</head>
<body>
  <h2>Login</h2>
  <form action="/login" method="POST">
    <label for="username">Username:</label><br>
    <input type="text" id="username" name="username" required><br><br>

    <label for="password">Password:</label><br>
    <input type="password" id="password" name="password" required><br><br>

    <button type="submit">Login</button>
  </form>

  <p>Don't have an account? <a href="register.html">Register here</a>.</p>
</body>
</html>
```

---

###  `register.html`

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Register</title>
</head>
<body>
  <h2>Register</h2>
  <form action="/register" method="POST">
    <label for="username">Username:</label><br>
    <input type="text" id="username" name="username" required><br><br>

    <label for="email">Email:</label><br>
    <input type="email" id="email" name="email" required><br><br>

    <label for="password">Password:</label><br>
    <input type="password" id="password" name="password" required><br><br>

    <button type="submit">Register</button>
  </form>

  <p>Already have an account? <a href="login.html">Login here</a>.</p>
</body>
</html>
```

---
