
## 🧩 What is Bootstrap?

**Bootstrap** is a popular open-source **CSS framework** used to build responsive, mobile-first websites quickly and efficiently.

### ✅ Key Features:

- Predefined **CSS classes** for layout, typography, buttons, forms, etc..
    
- Built-in **responsive grid system**.
    
- **JavaScript components** (like modals, carousels, tooltips).
    
- Easy integration with HTML — no need to write custom styles from scratch.
    

> Developed by Twitter engineers and currently maintained by the community.

---

## 📦 How to Install (Include) Bootstrap?

There are **three main methods** to include Bootstrap in your project:

### 1. ✅ **Using CDN (Content Delivery Network)** (Recommended for most projects)

- **`Bootstrap CDN: Delivering Bootstrap files (CSS, JS) from external servers for faster loading and easier integration.`**
- **`BS CDN: Utilizing a Content Delivery Network to serve Bootstrap assets, improving website performance and reducing server load.`**
- **`CDN for Bootstrap: Linking to remotely hosted Bootstrap resources, ensuring efficient delivery and potentially leveraging browser caching.`**
- **`External Bootstrap Libraries: Loading Bootstrap's CSS and JavaScript from a third-party CDN for optimal speed and bandwidth usage.`**

Include the following `<link>` in your `<head>`:

```
<!-- Bootstrap 5 CSS CDN -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
```

And the JS bundle (for interactive components):

```
<!-- Bootstrap JS Bundle (includes Popper.js) -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
```

---

### 2. 📥 **Installing via NPM (for advanced workflows)**

```
npm install bootstrap
```

Then include it in your CSS/JS files:

```
import 'bootstrap/dist/css/bootstrap.min.css';
import 'bootstrap/dist/js/bootstrap.bundle.min.js';
```

---

### 3. 💾 **Download and host manually**

- Download from [https://getbootstrap.com](https://getbootstrap.com).
    
- Link the CSS and JS files locally from your project folders.
    

---

## ❌ What Are the Drawbacks of Using Native CSS?

While writing plain (native) CSS gives full control, it has a few drawbacks:

### Drawbacks:

1. **Time-consuming** – You need to write and test styles for every component from scratch.
    
2. **Inconsistency** – Without a framework, UI elements may lack consistent spacing, size, and colors.
    
3. **Lack of responsiveness** – Native CSS requires more effort to make layouts work across devices.
    
4. **Repetition** – Common UI components (like buttons, cards, forms) need to be re-created for every project.
    
5. **Browser compatibility issues** – You’ll need to handle vendor prefixes and compatibility manually.
    

**Bootstrap solves most of these by providing a consistent and responsive design system.**

---

## 📐 What Is a Grid System?

A **grid system** in web design is a structure made up of rows and columns used to align and position elements on a page.

Bootstrap uses a **12-column responsive grid system** based on **Flexbox**.

---

### 🔹 How the Bootstrap Grid System Works:

- The main layout container is `.container` or `.container-fluid`.
    
- Inside the container, you use `.row` to create a horizontal group of columns.
    
- Columns are created using `.col`, `.col-6`, `.col-md-4`, etc.
    

---

### 🧱 Example:

```
<div class="container">
  <div class="row">
    <div class="col-md-6">
      <!-- Takes 6/12 columns on medium+ screens -->
      <p>Left Column</p>
    </div>
    <div class="col-md-6">
      <p>Right Column</p>
    </div>
  </div>
</div>
```

- `col-md-6` means "take 6 out of 12 columns on medium screens and larger".
    
- For responsive behavior, you can use:
    
    - `col-sm-*` for small screens
        
    - `col-md-*` for medium
        
    - `col-lg-*` for large
        
    - `col-xl-*` for extra-large
        

---

### 🔄 Example: Auto-responsive columns

```
<div class="row">
  <div class="col">One</div>
  <div class="col">Two</div>
  <div class="col">Three</div>
</div>
```

Each `.col` shares the space **equally**, regardless of screen size.

---

### 📱 Responsive Breakpoints (Bootstrap 5):

|Breakpoint|Class Prefix|Min Width|
|---|---|---|
|Extra Small|`col-`|`<576px`|
|Small|`col-sm-`|`≥576px`|
|Medium|`col-md-`|`≥768px`|
|Large|`col-lg-`|`≥992px`|
|Extra Large|`col-xl-`|`≥1200px`|
|XXL|`col-xxl-`|`≥1400px`|

----
- The Bootstrap **Grid System** and **breakpoints**
    
- How to **order**, **align**, and **offset** columns
    
- How to perform **horizontal** and **vertical alignment** in columns and rows
    

---

## 📐 The Grid System in Bootstrap

Bootstrap’s grid system is based on **12 columns** and built using **Flexbox**, allowing you to create responsive layouts quickly and flexibly.

---

## 🧱 Basic Grid Structure:

```
<div class="container">
  <div class="row">
    <div class="col">Column 1</div>
    <div class="col">Column 2</div>
  </div>
</div>
```

- `.container`: The layout wrapper.
    
- `.row`: A horizontal group of columns.
    
- `.col`: A flexible column that auto-sizes to fill space.
    

---

## 📊 Breakpoints in Bootstrap

These breakpoints define how the layout adapts to different screen sizes:

|Breakpoint|Class Prefix|Minimum Width|
|---|---|---|
|Extra Small|`col-`|`<576px`|
|Small|`col-sm-`|`≥576px`|
|Medium|`col-md-`|`≥768px`|
|Large|`col-lg-`|`≥992px`|
|Extra Large|`col-xl-`|`≥1200px`|
|Extra Extra Large|`col-xxl-`|`≥1400px`|

🔸 **Example:**

```
<div class="col-12 col-md-6">
  Full-width on small screens, half-width on medium+
</div>
```

---

## 🔃 Ordering Columns

You can control the **display order** using the `order-*` classes:

```
<div class="col order-2">Second</div>
<div class="col order-1">First</div>
```

You can also target breakpoints:

```
<div class="col order-md-3">Appears 3rd on medium+ screens</div>
```

---

## ⬅️ Offsetting Columns

Use `offset-*` classes to shift a column to the right by a number of columns:

```
<div class="col-md-4 offset-md-2">
  This starts after 2 empty columns
</div>
```

---

## 🔄 Horizontal Alignment (justify-content)

Apply these to the `.row` element to align columns horizontally:

|   |   |
|---|---|
|Class|Description|
|`justify-content-start`|Align left (default)|
|`justify-content-center`|Align center|
|`justify-content-end`|Align right|
|`justify-content-between`|Space between columns|
|`justify-content-around`|Equal space around columns|

```
<div class="row justify-content-center">
  <div class="col-4">Centered Column</div>
</div>
```

---

## ↕️ Vertical Alignment (align-items / align-self)

### On the row (for all children):

```
<div class="row align-items-center">
  <div class="col">Vertically centered column</div>
</div>
```

### On individual columns:

```
<div class="col align-self-end">
  Vertically aligned to bottom
</div>
```

---

## 🧪 Complete Example:

```
<div class="container">
  <div class="row align-items-center justify-content-between">
    <div class="col-md-4 order-md-2 offset-md-1">
      Offset, Ordered and Center Aligned
    </div>
    <div class="col-md-4">
      Regular Column
    </div>
  </div>
</div>
```

---## 💡 Bootstrap 5 Utility Classes

### 📝 Text Alignment & Style

|Class|Description|
|---|---|
|`text-center`|Centers text horizontally|
|`text-left`|Aligns text to the left _(start)_|
|`text-right`|Aligns text to the right _(end)_|
|`text-justify`|Justifies text|
|`text-uppercase`|Converts text to uppercase|
|`text-lowercase`|Converts text to lowercase|
|`text-capitalize`|Capitalizes each word|
|`font-italic`|Makes text italic|
|`font-weight-bold`|Applies bold font|
|`font-weight-bolder`|Bolder than bold|
|`font-weight-normal`|Normal font weight|
|`font-weight-light`|Light font weight|
|`font-weight-lighter`|Lighter than light|

> 🔹 **Note**: `text-left` and `text-right` are replaced with `text-start` and `text-end` in Bootstrap 5.

---

### 🎨 Background & Text Colors

|   |   |
|---|---|
|Class|Description|
|`bg-light`, `bg-dark`, `bg-primary`, `bg-secondary`|Background colors|
|`bg-danger`, `bg-success`, `bg-info`, `bg-warning`, `bg-white`|Alert/background types|
|`text-light`, `text-dark`, `text-danger`, `text-success`, `text-info`, `text-warning`, `text-white`, `text-muted`|Text color styling|

---

### 📦 Borders & Shadows

|   |   |
|---|---|
|Class|Description|
|`border`|Adds border to all sides|
|`border-bottom`|Border only at the bottom|
|`shadow`|Default shadow|
|`shadow-sm`|Small shadow|
|`shadow-lg`|Large shadow|
|`shadow-none`|Removes any shadow|
|`rounded`|Slightly rounded corners|
|`rounded-circle`|Perfect circle (e.g. for images)|

---

### 🧭 Position Utilities

|   |   |
|---|---|
|Class|Description|
|`position-relative`|Relative to normal position|
|`position-absolute`|Absolute to nearest positioned parent|
|`position-fixed`|Fixed to the viewport|
|`position-static`|Default static positioning|

---

### 📐 Spacing Utilities

Use `m` for margin and `p` for padding.  
Format: `m{side}-{breakpoint}-{size}`

Examples:

|   |   |
|---|---|
|Class|Description|
|`m-2`|Margin: 0.5rem on all sides|
|`p-3`|Padding: 1rem on all sides|
|`mt-4`|Margin-top: 1.5rem|
|`px-5`|Horizontal padding: 3rem|

---

### 🔘 Buttons

|   |   |
|---|---|
|Class|Description|
|`btn`|Base class for buttons|
|`btn-primary`, `btn-danger`, `btn-success`, etc.|Colored buttons|
|`btn-outline-primary`, etc.|Outlined version of buttons|

---

### 🖼️ Images

|   |   |
|---|---|
|Class|Description|
|`img-fluid`|Makes image responsive (100% width)|
|`img-thumbnail`|Adds border & padding (like a preview)|
|`rounded`, `rounded-circle`|Adds rounded or circular shape|

---

## 🏠 Example: Simple Home Page (Bootstrap 5)

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Home</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="bg-light text-center p-5">

  <div class="container">
    <h1 class="text-primary text-uppercase mb-4">Welcome Home</h1>
    <p class="text-muted font-italic">This is a simple homepage built with Bootstrap 5.</p>

    <img src="https://via.placeholder.com/150" class="img-thumbnail rounded-circle my-4" alt="Profile">

    <div class="d-grid gap-2 d-sm-flex justify-content-sm-center">
      <button class="btn btn-success me-2">Get Started</button>
      <button class="btn btn-outline-info">Learn More</button>
    </div>
  </div>

</body>
</html>
```

---
- **Bootstrap 5 components**: Alerts, Badges, Dropdowns, Cards, Media Objects
    
- How to **add a badge as an overlay on a card** (e.g., discount badge on products)
    

---

## 🎯 Bootstrap Components Overview

### ✅ Alerts

Used to provide feedback messages like success, warning, or errors.

```
<div class="alert alert-success" role="alert">
  Operation successful!
</div>

<div class="alert alert-link" role="alert">
  Login!
</div>
```

|Type|Class|
|---|---|
|Success|`alert-success`|
|Danger|`alert-danger`|
|Warning|`alert-warning`|
|Info|`alert-info`|

---

### 🔖 Badges

Used for counters, labels, or highlights.

```
<span class="badge bg-primary">New</span>
```

|   |   |
|---|---|
|Type|Class|
|Primary|`bg-primary`|
|Success|`bg-success`|
|Danger|`bg-danger`|
|Warning|`bg-warning`|
|Info|`bg-info`|

🔹 You can also use badges with headings or buttons:

```
<h4>Inbox <span class="badge bg-danger">4</span></h4>
```

---

### ⬇️ Dropdowns

Simple interactive dropdown menus:

```
<div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" data-bs-toggle="dropdown">
    Actions
  </button>
  <ul class="dropdown-menu">
    <li><a class="dropdown-item" href="#">Edit</a></li>
    <li><a class="dropdown-item" href="#">Delete</a></li>
  </ul>
</div>
```

---

### 🃏 Cards

Used for building blocks of content like profiles, products, or posts.

```
<div class="card" style="width: 18rem;">
  <img src="..." class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
```

---

### 🎥 Media Object 

Used to align an image and text side by side using Flexbox utilities.

```
<div class="d-flex align-items-start">
  <img src="https://via.placeholder.com/64" class="me-3 rounded" alt="User avatar" width="64" height="64">
  <div>
    <h5 class="mt-0 mb-1">Media heading</h5>
    <p>This is some text placed beside the image. You can also include links, buttons, or other elements here as needed.</p>
  </div>
</div>
```

---

### 🔍 Explanation:

- `**d-flex**`: Enables Flexbox layout.
    
- `**align-items-start**`: Aligns the image and content to the top vertically.
    
- `**me-3**`: Adds right spacing (margin-end) between the image and text.
    
- `**rounded**`: Gives the image rounded corners.
    
- `**mt-0**` **&** `**mb-1**`: Adjusts vertical spacing for the heading.

---

## 🏷️ Adding a Badge Overlay to a Card (like product discount)

You can place a badge in a card using **position utilities**:

```
<div class="card position-relative" style="width: 18rem;">
  <img src="https://via.placeholder.com/300" class="card-img-top" alt="Product Image">

  <!-- Badge overlay -->
  <span class="badge bg-danger position-absolute top-0 start-0 m-2">-30%</span>

  <div class="card-body">
    <h5 class="card-title">Product Name</h5>
    <p class="card-text">$70.00</p>
    <a href="#" class="btn btn-success">Buy Now</a>
  </div>
</div>
```

🧩 Breakdown:

- `position-relative` → applied to `.card` as a container
    
- `position-absolute` → on the `.badge` to position it on the card
    
- `top-0 start-0 m-2` → positions the badge in the top-left corner with margin
    

---
### 🏷️ About Us Webpage 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>About Us</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="bg-white text-dark">

  <div class="container py-5">

    <h1 class="text-center text-primary mb-4">About Us</h1>

    <div class="row align-items-center">
      <div class="col-md-6 mb-4 mb-md-0">
        <img src="img/image" class="img-fluid rounded shadow" alt="About Image">
      </div>
      <div class="col-md-6">
        <h3 class="mb-3">Who We Are</h3>
        <p class="text-muted">
          We are a passionate team dedicated to building meaningful digital experiences. 
          Our focus is on quality, innovation, and customer satisfaction. With years of industry experience, 
          we bring your ideas to life using modern web technologies.
        </p>

        <h5 class="mt-4">Our Mission</h5>
        <p class="text-muted">
          To deliver high-quality solutions that drive value and success for our clients, 
          and to foster long-lasting relationships based on trust and performance.
        </p>

        <button class="btn btn-success mt-3">Contact Us</button>
      </div>
    </div>

  </div>

</body>
</html>
```

---

🧩 **Key Features Used**:
- `container`, `row`, and `col-md-*` for layout
- `img-fluid`, `rounded`, `shadow` for image styling
- `text-primary`, `text-muted`, `btn-success` for colors and buttons
- No navigation bar included
- ---
## 📂 Collapse Component

The **collapse component** is used to toggle visibility of content (like accordions or hidden sections):

```
<button class="btn btn-primary" data-bs-toggle="collapse" data-bs-target="#info">
  Toggle Info
</button>

<div id="info" class="collapse mt-2">
  <div class="card card-body">
    This is hidden info!
  </div>
</div>
```

> 💡 Use `show` class to make it visible by default.

---

## 📋 Forms 

Bootstrap makes form styling and layout easy using utility classes.

### 🧱 Stacked Forms (Default)

Each input appears in a new line (block-level):

```
<form>
  <div class="mb-3">
    <label for="name" class="form-label">Name</label>
    <input type="text" class="form-control" id="name">
  </div>
  <div class="mb-3">
    <label for="email" class="form-label">Email address</label>
    <input type="email" class="form-control" id="email">
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>
```

---

### 📏 Inline Forms

Inputs are in one line (for small forms like login, search, etc.):

```
<form class="row row-cols-lg-auto g-3 align-items-center">
  <div class="col-12">
    <input type="text" class="form-control" placeholder="Username">
  </div>
  <div class="col-12">
    <input type="password" class="form-control" placeholder="Password">
  </div>
  <div class="col-12">
    <button type="submit" class="btn btn-success">Login</button>
  </div>
</form>
```

---

### 🧩 Grid System in Forms

You can apply the grid layout to forms to control label/input alignment:

```
<form>
  <div class="row mb-3">
    <label for="firstName" class="col-sm-2 col-form-label">First Name</label>
    <div class="col-sm-10">
      <input type="text" class="form-control" id="firstName">
    </div>
  </div>
  <div class="row mb-3">
    <label for="email" class="col-sm-2 col-form-label">Email</label>
    <div class="col-sm-10">
      <input type="email" class="form-control" id="email">
    </div>
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>
```

> ✅ Use `row`, `col-sm-*`, and `col-form-label` for responsive form layouts.

---

## 🎠 Carousel Component

Used to show image slides (banners, galleries):

```
<div id="carouselExample" class="carousel slide" data-bs-ride="carousel">
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img src="https://via.placeholder.com/800x300" class="d-block w-100" alt="...">
    </div>
    <div class="carousel-item">
      <img src="https://via.placeholder.com/800x300/cccccc" class="d-block w-100" alt="...">
    </div>
  </div>
  <button class="carousel-control-prev" data-bs-target="#carouselExample" data-bs-slide="prev">
    <span class="carousel-control-prev-icon"></span>
  </button>
  <button class="carousel-control-next" data-bs-target="#carouselExample" data-bs-slide="next">
    <span class="carousel-control-next-icon"></span>
  </button>
</div>
```

> 🎯 Use `carousel-item active` for the first slide, and `d-block w-100` on images.

---

## 📊 Tables

Basic styled table:

```
<table class="table table-striped table-hover table-bordered">
  <thead class="table-dark">
    <tr>
      <th>#</th>
      <th>Name</th>
      <th>Email</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Jane Doe</td>
      <td>jane@example.com</td>
    </tr>
    <tr>
      <td>2</td>
      <td>John Smith</td>
      <td>john@example.com</td>
    </tr>
  </tbody>
</table>
```

|Utility Class|Purpose|
|---|---|
|`table-striped`|Alternate row colors|
|`table-hover`|Highlight on hover|
|`table-bordered`|Add borders|
|`table-dark`|Dark header row|-

---
## 🧭 Navigation Concepts

Navigation is the system that allows users to explore and interact with a website. It’s categorized into three main types:

### 1. **Structural Navigation**

- Reflects the structure (hierarchy) of the website.
    
- Usually includes links like: Home, About, Services, Contact.
    
- Implemented as top or side navigation bars.
    

### 2. **Associative Navigation**

- Links related content together.
    
- Example: "Related Articles", "You Might Also Like", tags and categories.
    
- Often found at the bottom of posts or in sidebars.
    

### 3. **Utility Navigation**

- Offers access to utilities and tools (not part of main content).
    
- Examples: Login, Register, Language Switcher, Profile, Cart.
    
- Usually located at the top-right corner of the page.
    

---

## 🧱  Navigation Bars

Bootstrap makes it easy to create responsive navigation bars with minimal code.

### 🔹 Basic Navbar Example

```
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Brand</a>

    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav me-auto">
        <li class="nav-item">
          <a class="nav-link active" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Features</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Pricing</a>
        </li>
      </ul>
      <div class="d-flex">
        <a class="btn btn-outline-primary me-2" href="#">Login</a>
        <a class="btn btn-primary" href="#">Sign Up</a>
      </div>
    </div>
  </div>
</nav>
```

> 📝 Add `.navbar-light` or `.navbar-dark` depending on background color, and use `.bg-*` classes to style.

---

## 🍞 Breadcrumb 

**Breadcrumbs** show the user’s current location within the hierarchy of a site and allow easy navigation back to parent pages.

### 🔹 Basic Breadcrumb Example

```
<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item"><a href="#">Library</a></li>
    <li class="breadcrumb-item active" aria-current="page">Data</li>
  </ol>
</nav>
```

### 🔸 Breadcrumb Key Classes

|Class|Purpose|
|---|---|
|`.breadcrumb`|Parent container|
|`.breadcrumb-item`|Each breadcrumb step|
|`.active`|Marks the current location|
|`aria-current`|For accessibility and SEO|

> ✅ Use breadcrumbs especially in multi-level websites like dashboards, shops, and admin panels.

---

### 🛒 E-Commerce Home Page 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>E-Shop | Home</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" />
</head>
<body>

  <!-- 🔝 Navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">E-Shop</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse justify-content-between" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item"><a class="nav-link active" href="#">Home</a></li>
          <li class="nav-item"><a class="nav-link" href="#">Categories</a></li>
          <li class="nav-item"><a class="nav-link" href="#">Deals</a></li>
        </ul>
        <form class="d-flex">
          <input class="form-control me-2" type="search" placeholder="Search products" />
          <button class="btn btn-outline-light" type="submit">Search</button>
        </form>
        <div>
          <a class="btn btn-light ms-3" href="#">Login</a>
        </div>
      </div>
    </div>
  </nav>

  <!-- 🏷️ Popular Tags -->
  <div class="container mt-4">
    <h5>Popular Tags</h5>
    <div>
      <span class="badge bg-primary me-1">#Smartphones</span>
      <span class="badge bg-secondary me-1">#Laptops</span>
      <span class="badge bg-success me-1">#Accessories</span>
      <span class="badge bg-danger me-1">#Cameras</span>
      <span class="badge bg-warning text-dark me-1">#Gaming</span>
    </div>
  </div>

  <!-- 🧭 Category Navigation -->
  <div class="container mt-4">
    <h5>Shop by Category</h5>
    <div class="row">
      <div class="col-md-2"><a href="#" class="btn btn-outline-primary w-100 mb-2">Phones</a></div>
      <div class="col-md-2"><a href="#" class="btn btn-outline-secondary w-100 mb-2">Laptops</a></div>
      <div class="col-md-2"><a href="#" class="btn btn-outline-success w-100 mb-2">Accessories</a></div>
      <div class="col-md-2"><a href="#" class="btn btn-outline-danger w-100 mb-2">TVs</a></div>
      <div class="col-md-2"><a href="#" class="btn btn-outline-warning text-dark w-100 mb-2">Cameras</a></div>
    </div>
  </div>

  <!-- 🛍️ Product Cards -->
  <div class="container mt-4">
    <h5>Featured Products</h5>
    <div class="row row-cols-1 row-cols-md-3 g-4">
      <div class="col">
        <div class="card h-100 shadow-sm">
          <img src="https://via.placeholder.com/300x200" class="card-img-top" alt="Product 1">
          <div class="card-body">
            <h6 class="card-title">Wireless Earbuds</h6>
            <p class="card-text text-muted">$39.99</p>
            <a href="#" class="btn btn-sm btn-primary">Add to Cart</a>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card h-100 shadow-sm">
          <img src="https://via.placeholder.com/300x200" class="card-img-top" alt="Product 2">
          <div class="card-body">
            <h6 class="card-title">Gaming Laptop</h6>
            <p class="card-text text-muted">$999.99</p>
            <a href="#" class="btn btn-sm btn-primary">Add to Cart</a>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card h-100 shadow-sm">
          <img src="https://via.placeholder.com/300x200" class="card-img-top" alt="Product 3">
          <div class="card-body">
            <h6 class="card-title">4K Action Camera</h6>
            <p class="card-text text-muted">$79.99</p>
            <a href="#" class="btn btn-sm btn-primary">Add to Cart</a>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- 🦶 Footer -->
  <footer class="bg-dark text-white mt-5 p-4 text-center">
    &copy; 2025 E-Shop. All rights reserved.
  </footer>

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

---
