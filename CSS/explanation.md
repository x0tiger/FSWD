# CSS - Cascading Style Sheets

## What is CSS?

CSS (**Cascading Style Sheets**) is a language used to control the **appearance and layout** of web pages. It allows you to change colors, fonts, spacing, sizes, element positions, layouts, and more..

---

## 📝 How to Create CSS Files

### 1. **External CSS File**

- You create a separate `.css` file.
    
- Link it in your HTML file using the `<link>` tag inside the `<head>`.
    

**Example:**

```
<link rel="stylesheet" href="style.css">
```

**Content of** `**style.css**`**:**

```
body {
  background-color: #f0f0f0;
  font-family: Arial, sans-serif;
}
```

---

### 2. **Internal CSS**

- Write CSS inside a `<style>` tag in the HTML `<head>` section.
    

**Example:**

```
<head>
  <style>
    h1 {
      color: blue;
    }
  </style>
</head>
```

---

### 3. **Inline CSS**

- CSS written directly inside an element using the `style` attribute.
    

**Example:**

```
<p style="color: red; font-size: 18px;">Styled text</p>
```

---

## ⚖️ Comparing CSS Methods

| Method          | Easy to Update | Performance | Priority (Power)              | Reusability    |
| --------------- | -------------- | ----------- | ----------------------------- | -------------- |
| Browser Default | ❌ No control   | Low         | Weakest                       | ❌ None         |
| External File   | ✅ Very easy    | Good        | Lower                         | ✅ High         |
| Internal Style  | ✅ Easy         | Medium      | Higher than external          | ⚠️ Limited     |
| Inline Style    | ❌ Hard         | Poor        | Highest (except `!important`) | ❌ Very limited |

---

## 🧱 CSS Rules, Properties, and Values

- A **rule** in CSS is a combination of a **selector** and a **block of declarations**.
    
- A **property** defines what you want to style (e.g. `color`).
    
- A **value** is what you assign to that property (e.g. `red`).
    

**Example:**

```
p {
  color: red;
  font-size: 16px;
}
```

Explanation:

- `p` → **selector**
    
- `color`, `font-size` → **properties**
    
- `red`, `16px` → **values**
    

---

## 🎯 Different Types of Selectors

### 1. **Universal Selector** (`*`)

Targets **all** elements.

```
* {
  margin: 0;
  padding: 0;
}
```

---

### 2. **Element (Tag) Selector**

Targets specific HTML tags.

```
h1 {
  color: green;
}
```

---

### 3. **ID Selector**

Targets an element with a specific `id`.

**HTML:**

```
<div id="header"></div>
```

**CSS:**

```
#header {
  background-color: black;
}
```

---

### 4. **Class Selector**

Targets elements that share the same class.

**HTML:**

```
<p class="note">Note text</p>
```

**CSS:**

```
.note {
  color: orange;
}
```

---

## 🔗 Combining Multiple Selectors

### Examples:

- Target all `<p>` inside `<div>`:
    

```
div p {
  color: purple;
}
```

- Target elements with both classes:
    

```
.alert.warning {
  background: yellow;
}
```

- Target multiple elements:
    

```
h1, h2, h3 {
  font-weight: bold;
}
```

---

## ❗ The `!important` Rule

Used to **force** a style to override any other rule, even if it normally has lower priority.

```
p {
  color: blue !important;
}
```

⚠️ **Warning:** Overusing `!important` can make your CSS hard to manage. Use only when truly necessary.

---

## 💬 CSS Comments

Use comments to leave notes or explanations inside your CSS code. They are ignored by the browser.

```
/* This is a comment */
body {
  background-color: white;
}
```

---

## 🥇 Precedence vs. Priority

### 1. **Precedence (Cascading Order)**

Depends on the **location** of the style:

- Inline > Internal > External
    
- The later a rule is defined, the more likely it is to override previous ones (unless specificity or `!important` is involved).
    

---

### 2. **Priority (Specificity)**

Specificity defines **which selector wins** when multiple rules target the same element.

From lowest to highest:

```
Universal (*) < Tag < Class < ID < Inline < !important
```

**Example:**

```
p {
  color: green;
}

.intro {
  color: blue;
}

#mainText {
  color: red;
}
```

**HTML:**

```
<p id="mainText" class="intro">Hello</p>
```

👉 The text will be **red**, because the ID selector has **higher specificity** than the class or tag selector.

---
## 🧬 Parent-Child & Sibling Selectors

CSS provides powerful **combinators** to define relationships between elements.

### 🔹 1. **Parent > Child Selector (**`**E > F**`**)**

Targets elements that are **direct children** of a specific parent.

**Example:**

```
div > p {
  color: blue;
}
```

Matches:

```
<div>
  <p> ✔ Direct child</p>
</div>

<section>
  <div>
    <p>❌ Not matched (not a direct child)</p>
  </div>
</section>
```

---

### 🔹 2. **Ancestor Descendant Selector (**`**E F**`**)**

Targets **all descendants**, not just direct children.

```
ul li {
  list-style-type: square;
}
```

Matches both:

```
<ul>
  <li>✔ Direct child</li>
  <li>
    <span><li>✔ Nested descendant</li></span>
  </li>
</ul>
```

---

### 🔹 3. **Adjacent Sibling Selector (**`**E + F**`**)**

Selects the **immediate next sibling**.

```
h1 + p {
  color: red;
}
```

Matches:

```
<h1>Title</h1>
<p>✔ This will be red</p>
```

Does **not** match:

```
<h1>Title</h1>
<span></span>
<p>❌ Skipped element in between</p>
```

---

### 🔹 4. **General Sibling Selector (**`**E ~ F**`**)**

Selects **all following siblings** of the same parent.

```
h1 ~ p {
  color: green;
}
```

Matches:

```
<h1>Heading</h1>
<p>✔ First paragraph</p>
<p>✔ Second paragraph</p>
```

---

## 🧩 Attribute Selectors

You can target elements based on their attributes and even specific values.

### ✅ Basic Format:

```
[attribute] {
  /* Styles here */
}
```

### 🔹 1. **Exists / Has Attribute**

Matches if the attribute is present, regardless of its value.

```
input[required] {
  border: 2px solid red;
}
```

---

### 🔹 2. **Exact Match (**`**=**`**)**

Matches if the attribute value is **exactly** the given string.

```
a[target="_blank"] {
  color: orange;
}
```

---

### 🔹 3. **Contains Substring (**`***=**`**)**

Matches if the attribute **contains** a given substring.

```
a[href*="example"] {
  text-decoration: underline;
}
```

Matches:

```
<a href="https://example.com">✔</a>
<a href="https://myexample.net">✔</a>
```

---

### 🔹 4. **Begins With (**`**^=**`**)**

Matches if the value **starts with** a certain string.

```
img[src^="https://"] {
  border: 1px solid green;
}
```

---

### 🔹 5. **Ends With (**`**$=**`**)**

Matches if the value **ends with** a certain string.

```
img[src$=".png"] {
  border: 1px solid blue;
}
```

---

### 🔹 6. **Hyphen-Separated (**`**|=**`**)**

Matches exact value or value followed by a **hyphen**.

```
div[lang|="en"] {
  font-style: italic;
}
```

Matches:

- `lang="en"`
    
- `lang="en-US"` But **not** `lang="english"`
    

---

### 🔹 7. **Whitespace-Separated (**`**~=**`**)**

Matches if the value is a **space-separated list** that contains the word.

```
[class~="button"] {
  padding: 10px;
}
```

Matches:

```
<div class="primary button large">✔</div>
```

---
## 🎨 Colors in CSS

CSS allows you to set colors using different **color models** and formats. Here are the main ones:

---

### 🔹 1. **Color Keywords**

Predefined names such as:

```
color: red;
color: blue;
color: transparent;
```

✅ Easy to use  
❌ Limited flexibility

---

### 🔹 2. **Hexadecimal (**`**#RRGGBB**`**)**

Represents red, green, and blue using hex values.

```
color: #ff0000; /* Red */
color: #00ff00; /* Green */
color: #0000ff; /* Blue */
```

🔸 You can also use shorthand:

```
#fff  →  #ffffff (white)
#000  →  #000000 (black)
```

---

### 🔹 3. **RGB (**`**rgb(r, g, b)**`**)**

Specifies red, green, blue components (0–255):

```
color: rgb(255, 0, 0); /* Red */
```

---

### 🔹 4. **RGBA (**`**rgba(r, g, b, a)**`**)**

Like RGB but adds **alpha transparency** (0 to 1):

```
color: rgba(255, 0, 0, 0.5); /* 50% transparent red */
```

---

### 🔹 5. **HSL (**`**hsl(hue, saturation, lightness)**`**)**

Hue in degrees (0–360), saturation/lightness as %:

```
color: hsl(120, 100%, 50%); /* Green */
```

---

### 🔹 6. **HSLA (**`**hsla(h, s, l, a)**`**)**

Like HSL with an alpha transparency value:

```
color: hsla(240, 100%, 50%, 0.5); /* 50% transparent blue */
```

---

## 📏 Dimensions in CSS

CSS uses **units** to measure things like width, height, padding, font size, etc.

---

### 🔹 Absolute Units (Fixed Size)

| Unit | Description            | Example            |
| ---- | ---------------------- | ------------------ |
| `px` | Pixels (most common)   | `width: 100px;`    |
| `in` | Inches                 | `width: 2in;`      |
| `cm` | Centimeters            | `width: 5cm;`      |
| `mm` | Millimeters            | `width: 20mm;`     |
| `pt` | Points (1 pt = 1/72in) | `font-size: 12pt;` |

🟢 Good for precision, but **not responsive**.

---

### 🔹 Relative Units (Responsive)

|       |                                     |                      |
| ----- | ----------------------------------- | -------------------- |
| Unit  | Based On                            | Example              |
| `%`   | Relative to parent size             | `width: 50%;`        |
| `em`  | Relative to parent’s font-size      | `font-size: 2em;`    |
| `rem` | Relative to root `<html>` font-size | `font-size: 1.5rem;` |
| `vw`  | 1% of viewport width                | `width: 50vw;`       |
| `vh`  | 1% of viewport height               | `height: 30vh;`      |

🟢 Great for responsiveness  
⚠️ Needs testing across screen sizes

---

## 🧱 Common CSS Properties

Here are some frequently used properties with examples:

---

### 🔸 `width` & `height`

Defines size of the element.

```
div {
  width: 300px;
  height: 200px;
}
```

---

### 🔸 `font-size`

Sets the size of text.

```
p {
  font-size: 16px;
}
```

---

### 🔸 `color`

Text color.

```
h1 {
  color: #333;
}
```

---

### 🔸 `background-color`

Background color of the element.

```
section {
  background-color: lightgray;
}
```

---

### 🔸 `opacity`

Controls the transparency level of an element. (0 = fully transparent, 1 = fully opaque)

```
img {
  opacity: 0.5;
}
```

You can also control color transparency with `rgba()` or `hsla()`.

--- 
## 📦 CSS Box Model

The **Box Model** is how browsers calculate the **space** each element takes on the page.

It consists of:

```
+---------------------------+
|       Margin              |
|  +---------------------+  |
|  |     Border          |  |
|  |  +--------------+   |  |
|  |  |  Padding     |   |  |
|  |  |  +--------+  |   |  |
|  |  |  | Content |  |   |  |
|  |  |  +--------+  |   |  |
|  |  +--------------+   |  |
|  +---------------------+  |
+---------------------------+
```

---

### 🔹 1. `width` & `height`

Control the size of the **content area only**.

```
div {
  width: 200px;
  height: 100px;
}
```

---

### 🔹 2. `padding`

Space **inside the element**, between content and border.

```
div {
  padding: 10px; /* adds space inside */
}
```

---

### 🔹 3. `border`

The line surrounding the padding.

```
div {
  border: 2px solid black;
}
```

---

### 🔹 4. `margin`

Space **outside the element**, between it and others.

```
div {
  margin: 20px; /* creates outer spacing */
}
```

---

## ✍️ Shorthand vs Longhand Notation

CSS allows both **longhand** and **shorthand** syntax:

### Longhand:

```
margin-top: 10px;
margin-right: 15px;
margin-bottom: 20px;
margin-left: 25px;
```

### Shorthand:

```
margin: 10px 15px 20px 25px;
/* Top Right Bottom Left */
```

Other shorthand formats:

```
margin: 10px;                 /* all sides */
margin: 10px 20px;            /* top/bottom, left/right */
margin: 10px 20px 30px;       /* top, left/right, bottom */
```

Same for `padding`, and `border-width`.

---

## 🟢 `border-radius`: Rounded Corners

### Basic Usage:

```
div {
  border-radius: 10px;
}
```

### Circular Image:

To make an image circular:

```
img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover; /* keeps image proportion */
}
```

**Requirements:**

- The image must be a **square** (equal width and height).
    
- `border-radius: 50%` makes it fully round.
    

---

## 📐 `display` Property

Controls **how an element behaves** in the layout.

---

### 🔹 `display: block`

- Takes up the full width
    
- Starts on a new line
    

```
div {
  display: block;
}
```

Examples: `<div>`, `<p>`, `<h1>` are block by default.

---

### 🔹 `display: inline`

- Only takes up as much width as needed
    
- Does **not** start on a new line
    

```
span {
  display: inline;
}
```

Examples: `<span>`, `<a>`, `<strong>`

---

### 🔹 `display: inline-block`

- Behaves like `inline` (flows with text), but allows **width**, **height**, **padding**, and **margin**.
    

```
button {
  display: inline-block;
  padding: 10px 20px;
}
```

---

### 🔹 `display: none`

- Completely **hides** the element (not even space is reserved).
    

```
div {
  display: none;
}
```

Useful for modals, dropdowns, toggles, etc.

---
## 🧱 Reviewing the `display` Property

|Value|Behavior|
|---|---|
|`block`|Takes full width, starts on a new line|
|`inline`|Fits content only, no width/height/padding/margin supported|
|`inline-block`|Behaves like inline but allows width, height, padding, etc.|
|`none`|Hides the element completely (removed from layout)|

---

### ✅ Comparison Table:

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|Property|New Line|Width/Height|Padding|Margin|Part of Flow|
|`block`|✔|✔|✔|✔|✔|
|`inline`|❌|❌|❌|❌|✔|
|`inline-block`|❌|✔|✔|✔|✔|
|`none`|❌|❌|❌|❌|❌|

---

## 🎯 How to Center Elements

### 🔹 Horizontally (Block Elements):

```
div {
  margin: 0 auto;
  width: 50%;
}
```

### 🔹 Horizontally (Text or Inline Elements):

```
p {
  text-align: center;
}
```

---

### 🔹 Vertically (Inline Elements):

```
span {
  vertical-align: middle;
}
```

---

### 🔹 Center Using Flexbox:

```
.container {
  display: flex;
  justify-content: center;  /* horizontal */
  align-items: center;      /* vertical */
  height: 100vh;
}
```

---

## 🧮 Simulating a Grid System

A simple grid using `float`:

```
.row {
  overflow: hidden;
}
.col {
  float: left;
  width: 33.33%; /* 3 columns */
  padding: 10px;
}
```

Or use `flexbox`:

```
.row {
  display: flex;
}
.col {
  flex: 1;
}
```

---

## 🏄 `float` and `clear` Properties

### 🔹 `float`

- Moves elements to the left or right, removing them from normal flow.
    

```
img {
  float: left;
}
```

### 🔹 `clear`

- Prevents elements from wrapping around floated elements.
    

```
.clearfix {
  clear: both;
}
```

### ✅ Comparison:

|   |   |
|---|---|
|Property|Description|
|`float: left`|Floats element to the left|
|`float: right`|Floats element to the right|
|`clear: left`|Stops float wrapping from left|
|`clear: right`|Stops float wrapping from right|
|`clear: both`|Stops wrapping from both sides|

---

## 📍 `position` Property

### 🔹 `static` (default)

Element is in the normal document flow.

### 🔹 `relative`

Position relative to itself (can nudge it using top/right/bottom/left).

```
div {
  position: relative;
  top: 10px;
  left: 20px;
}
```

### 🔹 `absolute`

Position relative to the nearest **non-static ancestor**.

```
div {
  position: absolute;
  top: 0;
  right: 0;
}
```

### 🔹 `fixed`

Stays in place **even when scrolling** — relative to the viewport.

```
div {
  position: fixed;
  bottom: 10px;
  right: 10px;
}
```

---

## 🧭 Positioning Examples

### 🔹 Bottom Right Corner:

```
.element {
  position: fixed;
  bottom: 0;
  right: 0;
}
```

### 🔹 Center of Screen:

Using Flexbox:

```
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

Using `position` + `transform`:

```
.element {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

---

## ➗ Using the `calc()` Function

The `calc()` function allows for dynamic calculations:

```
width: calc(100% - 50px);
font-size: calc(1rem + 2px);
```

🟡 You must have **spaces** around operators:

```
/* Correct */
width: calc(100% - 20px);
/* Incorrect */
width: calc(100%-20px);
```

---## 🅰️ Font and Text Properties

### 🔹 `font-family`

Specifies the typeface of the text.

```
p {
  font-family: 'Arial', sans-serif;
}
```

- Multiple values can be used as a fallback.
    
- If the first font is unavailable, the browser will try the next.
    

---

### 🔹 `font-weight`

Defines the thickness of the font.

```
p {
  font-weight: bold; /* Can be normal, bold, or numeric values (100-900) */
}
```

Common values:

- `normal`, `bold`, `lighter`, `bolder`
    
- Numeric range from `100` (thin) to `900` (thick)
    

---

### 🔹 `font-size`

Specifies the size of the text.

```
p {
  font-size: 16px;
}
```

Can use units like `px`, `em`, `%`, `rem`, and `vw` for responsiveness.

---

### 🔹 `font-variant`

Controls the appearance of text in a more advanced way (like small caps).

```
p {
  font-variant: small-caps;
}
```

### 🔹 `font-style`

Defines the style of the font (italic, normal, oblique).

```
p {
  font-style: italic;
}
```

---

### 🔹 `text-align`

Aligns the text horizontally inside an element.

```
p {
  text-align: center; /* left, center, right, justify */
}
```

---

### 🔹 `text-shadow`

Applies shadow effects to text.

```
h1 {
  text-shadow: 2px 2px 5px #888888;
}
```

- Values: `horizontal shadow`, `vertical shadow`, `blur radius`, `color`
    

---

### 🔹 `box-shadow`

Applies shadow effects to elements (not just text).

```
div {
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
}
```

- Values: `horizontal offset`, `vertical offset`, `blur radius`, `spread radius`, `color`
    

---

### 🔹 `text-decoration`

Specifies text decoration (underline, line-through, etc.).

```
a {
  text-decoration: underline;
}
```

Common values:

- `none`, `underline`, `overline`, `line-through`, `blink` (deprecated)
    

---

### 🔹 `text-indent`

Indents the first line of text.

```
p {
  text-indent: 30px;
}
```

---

### 🔹 `letter-spacing`

Controls the spacing between characters.

```
h1 {
  letter-spacing: 2px;
}
```

---

### 🔹 `word-spacing`

Controls the spacing between words.

```
p {
  word-spacing: 5px;
}
```

---

## 📝 List Styling Properties

### 🔹 `list-style-type`

Specifies the type of list marker for an ordered (`<ol>`) or unordered (`<ul>`) list.

```
ul {
  list-style-type: square; /* Can be circle, disc, square, decimal, etc. */
}
```

### 🔹 `list-style-image`

Defines an image to use as a bullet point for list items.

```
ul {
  list-style-image: url('bullet.png');
}
```

### 🔹 `list-style-position`

Specifies the position of the list marker in relation to the list items.

```
ul {
  list-style-position: inside; /* 'outside' is default */
}
```

---

### ✅ Comparison Between List Styling Properties:

|Property|Unordered List (`<ul>`)|Ordered List (`<ol>`)|
|---|---|---|
|`list-style-type`|`circle`, `square`, `disc`|`decimal`, `upper-roman`|
|`list-style-image`|Custom images as bullet|Custom images as marker|
|`list-style-position`|`inside`, `outside`|`inside`, `outside`|

---

## 📦 `box-sizing` Property

### 🔹 `content-box` (default)

The width and height **do not** include padding and borders. Only the content area is measured.

```
div {
  box-sizing: content-box;
  width: 100px;
  padding: 20px;
  border: 5px solid black;
}
```

- Total width: `100px + 20px (padding) + 5px (border)` = `150px`.
    

---

### 🔹 `border-box`

The width and height **include** padding and borders. Makes it easier to control the total size of elements.

```
div {
  box-sizing: border-box;
  width: 100px;
  padding: 20px;
  border: 5px solid black;
}
```

- Total width: `100px` (includes padding and borders).
    

---

### 🔹 `padding-box`

The width and height include **padding**, but not borders.

```
div {
  box-sizing: padding-box;
  width: 100px;
  padding: 20px;
  border: 5px solid black;
}
```

- Total width: `100px + 20px (padding)` = `120px` (borders are not included).
    

---

### ✅ Comparison of `box-sizing` Values:

|               |          |          |                                               |
| ------------- | -------- | -------- | --------------------------------------------- |
| Property      | Padding  | Border   | Total Width/Height                            |
| `content-box` | Excluded | Excluded | Adds padding and border to width/height       |
| `border-box`  | Included | Included | Width/height is the same as the declared size |
| `padding-box` | Included | Excluded | Width/height includes padding but not borders |

---
## 🌐 How to Use Google Fonts

To use Google Fonts:

1. **Choose a font** from [Google Fonts](https://fonts.google.com/).
    
2. **Embed the link** in your HTML `<head>` section:
    

```
<head>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
</head>
```

3. **Use the font** in your CSS:
    

```
body {
  font-family: 'Roboto', sans-serif;
}
```

---

## 🖼️ How to Set a Full-Cover Background Image

To set a background image that covers the full viewport:

```
body {
  background-image: url('background.jpg');
  background-size: cover; /* Ensures the image covers the entire area */
  background-position: center; /* Centers the image */
  background-attachment: fixed; /* Fixes the image in place while scrolling */
}
```

---

## 🎥 How to Set a Full-Cover Background Video

To set a video as the background:

```
<video autoplay muted loop id="bg-video">
  <source src="background.mp4" type="video/mp4">
</video>

<style>
  #bg-video {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1; /* Ensures the video stays behind content */
  }
</style>
```

- The `autoplay`, `muted`, and `loop` attributes ensure continuous playback.
    
- The `object-fit: cover` ensures the video covers the screen.
    

---

## 🖤 How to Apply Filters in CSS

CSS filters allow you to apply visual effects like grayscale or blur to images, elements, or backgrounds.

### 🔹 `grayscale` Filter

Converts the element to grayscale (black and white).

```
img {
  filter: grayscale(100%);
}
```

- `100%` is fully grayscale, `0%` is normal color.
    

---

### 🔹 `blur` Filter

Applies a blur effect to an element.

```
img {
  filter: blur(5px);
}
```

- You can use `px` to define the blur radius.
    

---

## 🧩 Advanced Selectors: Pseudo-Classes and Pseudo-Elements

### 🔹 **Pseudo-Classes**:

Pseudo-classes apply styles to elements based on their state or position, such as when an element is hovered over or focused.

```
a:hover {
  color: red; /* Changes color when the link is hovered */
}
```

### Common Pseudo-Classes:

- `:link` — Targets unvisited links.
    
- `:visited` — Targets visited links.
    
- `:hover` — When the element is hovered over.
    
- `:focus` — When an element is focused (e.g., `<input>`).
    
- `:active` — When the element is being clicked.
    
- `:nth-child(n)` — Selects an element based on its position.
    
- `:not(selector)` — Selects elements that don't match a specific selector.
    

Example using `:nth-child`:

```
ul li:nth-child(odd) {
  background-color: lightgray;
}
```

---

### 🔹 **Pseudo-Elements**:

Pseudo-elements target specific parts of an element, such as the first letter or line.

```
p::first-letter {
  font-size: 2em;
  color: red;
}
```

### Common Pseudo-Elements:

- `::first-letter` — Selects the first letter of the text.
    
- `::first-line` — Selects the first line of the text.
    
- `::before` — Inserts content before the element's actual content.
    
- `::after` — Inserts content after the element's actual content.
    

Example using `::before` and `::after`:

```
h1::before {
  content: '★';
}
h1::after {
  content: '★';
}
```

- `content` property is used to insert text or other content.
    

---

## 📏 `z-index` Property

The `z-index` property controls the stacking order of elements. Higher `z-index` values are placed on top of lower ones.

### Syntax:

```
.element {
  position: relative; /* or absolute, fixed */
  z-index: 10;
}
```

### Example:

```
div.box1 {
  position: absolute;
  z-index: 1;
  top: 50px;
  left: 50px;
  width: 100px;
  height: 100px;
  background-color: red;
}

div.box2 {
  position: absolute;
  z-index: 2; /* Will appear on top of box1 */
  top: 100px;
  left: 100px;
  width: 100px;
  height: 100px;
  background-color: blue;
}
```

- The `z-index` only works on elements with a **positioning context** (`relative`, `absolute`, `fixed`, or `sticky`).
    

### Key Notes:

- Default `z-index` is `auto` (essentially `0`).
    
- Elements with a higher `z-index` will overlap elements with a lower `z-index`.
    
- `z-index` works within stacking contexts.
    

---## 🔄 How to Apply Transitions and Transforms

### 🔹 **Transitions**

CSS transitions allow you to change property values smoothly (over a duration) when an element is interacted with (e.g., hover, focus).

#### Example of a transition:

```
button {
  background-color: blue;
  transition: background-color 0.3s ease; /* Duration of 0.3s */
}

button:hover {
  background-color: red;
}
```

In the example above, the background color changes smoothly when you hover over the button. The transition takes **0.3 seconds** and uses the **ease** timing function.

---

### 🔹 **Transforms**

Transforms enable you to manipulate an element's size, shape, and position on the page without affecting its layout.

#### Types of transforms:

1. **translate()** — Moves the element along the X and Y axes.
    

```
div {
  transform: translate(50px, 100px); /* Moves the element 50px right and 100px down */
}
```

2. **rotate()** — Rotates the element by a specified degree.
    

```
div {
  transform: rotate(45deg); /* Rotates the element 45 degrees clockwise */
}
```

3. **scale()** — Changes the size of the element.
    

```
div {
  transform: scale(1.5); /* Increases the size by 1.5 times */
}
```

4. **skew()** — Skews the element along the X and Y axes.
    

```
div {
  transform: skew(20deg, 10deg); /* Skews the element 20 degrees horizontally and 10 degrees vertically */
}
```

You can combine multiple transforms:

```
div {
  transform: translate(50px, 100px) rotate(45deg);
}
```

---

## 🌐 What Are Vendor Prefixes and How to Apply Them?

Vendor prefixes are used to ensure that CSS properties and features are applied correctly across different browsers, especially when a feature is not fully supported yet.

### Example of vendor prefixes:

```
/* For Chrome, Safari, and Opera */
.element {
  -webkit-transform: rotate(45deg); /* Safari and older Chrome */
  transform: rotate(45deg);
}

/* For Firefox */
.element {
  -moz-transform: rotate(45deg); /* Firefox */
  transform: rotate(45deg);
}
```

- `-webkit-` (Chrome, Safari, Opera)
    
- `-moz-` (Firefox)
    
- `-ms-` (Internet Explorer)
    
- `-o-` (Opera)
    

**Note:** Always use the standard property without a prefix after the vendor-prefixed versions to ensure future compatibility.

---

## 🌍 What is the "Can I Use?" Website?

The **"Can I Use?"** website ([caniuse.com](https://caniuse.com/)) is a resource for checking the browser support of web technologies, including HTML, CSS, JavaScript, and more.

### Features:

- **Compatibility tables** for browser features and technologies.
    
- You can search for a specific feature (like `flexbox` or `grid`).
    
- Provides **global support** data and shows **which browsers support a specific feature** and which versions.
    
- Offers **tools to view detailed browser statistics**.
    

---

## ⚙️ What are "Reset CSS" and "Normalize CSS"?

### 🔹 **Reset CSS**

A reset stylesheet removes all default browser styling, ensuring consistent styling across all browsers.

#### Example of a basic reset:

```
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

This ensures that all elements have no margin or padding by default, and it normalizes the box model across browsers.

---

### 🔹 **Normalize CSS**

Normalize CSS is a modern approach to making HTML elements look consistent across all browsers while preserving useful default styling.

It **does not remove all default styles** but **normalizes** inconsistent behavior (like margin/padding differences or font styling).

You can use Normalize.css to include it in your projects.

---
