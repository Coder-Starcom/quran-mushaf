---
title: "[02] - 04 - Understanding styles.css"
datePublished: Wed Aug 28 2024 21:00:00 GMT+0000 (Coordinated Universal Time)
cuid: cmcqh2ma9000202jp7e0s5kq1
slug: 02-04-understanding-stylescss
tags: css

---

Your `styles.css` defines the **look and feel** of the entire app—from colors and fonts to layout and animations. Here’s a detailed walk-through, grouped into logical parts:

---

### 🖋️ 1. Fonts and Variables

```css
@import url("https://fonts.googleapis.com/css?family=Open+Sans|Roboto:400,700&display=swap");
```

✅ Loads two professional fonts from Google Fonts:

* `Roboto`: Headlines
    
* `Open Sans`: Body text
    

```css
:root {
  --clr-primary-1: hsl(205, 86%, 17%);
  --clr-grey-1: hsl(209, 61%, 16%);
  ...
  --ff-primary: "Roboto", sans-serif;
  --ff-secondary: "Open Sans", sans-serif;
  ...
}
```

✅ `:root` defines **CSS variables** (custom properties) for:

* Color palette: Primary shades, greys, white, etc.
    
* Fonts and spacing
    
* Box shadows, max-widths, radius, etc.
    

🧠 **Why use variables?**

> You can change the whole color scheme or font with just one edit—super maintainable!

---

### 🌍 2. Global Styles

```css
*,
::after,
::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

✅ Resets default spacing and fixes layout bugs

```css
body {
  font-family: var(--ff-secondary);
  background: var(--clr-grey-10);
  color: var(--clr-grey-1);
}
```

✅ Default font is set, background is light grey, text is dark grey

```css
h1, h2, h3, h4 {
  letter-spacing: var(--spacing);
  font-family: var(--ff-primary);
}
```

✅ Headings use `Roboto` and spaced lettering for elegance

---

### 🎛️ 3. Buttons

```css
.btn {
  text-transform: uppercase;
  ...
  border-radius: var(--radius);
}
.btn:hover {
  background: var(--clr-black);
  color: var(--clr-white);
}
```

✅ Buttons are bold, uppercase, bordered, and hoverable

```css
.btn-white {
  border-color: var(--clr-white);
  color: var(--clr-white);
}
.btn:hover {
  background: var(--clr-white);
  color: var(--clr-secondary);
}
```

✅ `btn-white` is used in the hero section — elegant white outline on dark overlay

---

### 🧭 4. Navbar

```css
nav {
  background: var(--clr-white);
  padding: 1rem 1.5rem;
}
.fixed-nav {
  position: fixed;
  top: 0;
  ...
  box-shadow: var(--light-shadow);
}
```

✅ Sticky navbar with a smooth scroll + elegant shadow on scroll

```css
.nav-toggle {
  font-size: 1.5rem;
  background: transparent;
  cursor: pointer;
}
.links-container {
  height: 0;
  overflow: hidden;
  transition: var(--transition);
}
.show-links {
  height: 200px;
}
```

✅ Responsive hamburger menu that expands and collapses with animation

---

### 📱 5. Responsive Nav on Desktop

```css
@media screen and (min-width: 800px) {
  .nav-center {
    display: flex;
    justify-content: space-between;
  }
  .nav-toggle {
    display: none;
  }
  .links {
    display: flex;
  }
  .links a {
    color: var(--clr-white);
  }
}
```

✅ Navbar switches to horizontal layout on wider screens

---

### 🌅 6. Hero Banner

```css
header {
  min-height: 100vh;
  background: linear-gradient(...), url(./hero-bcg.jpeg) center/cover no-repeat;
}
```

✅ Full-screen header with a **dark overlay** and a **background image**

```css
.banner {
  display: grid;
  place-items: center;
  text-align: center;
}
```

✅ Text is centered in the hero area using `grid`

---

### 📦 7. Sections: About, Services, Tours

```css
#about,
#services,
#tours {
  height: 80vh;
}
```

✅ Fixed heights, but later overridden with:

```css
#services,
#tours {
  height: fit-content;
}
```

✅ Now adjusts height automatically based on content

```css
.section-center {
  width: 90vw;
  margin: 0 auto;
  max-width: 1170px;
  display: grid;
  gap: 3rem 2rem;
}
.menu-item {
  display: grid;
  max-width: 25rem;
}
```

✅ Tour cards are laid out in **grid**, responsive and centered

```css
.photo {
  height: 200px;
  object-fit: cover;
  border: 0.25rem solid var(--clr-gold);
  border-radius: var(--radius);
}
```

✅ Beautiful images with golden border and rounded edges

---

### 🎯 8. Filter Buttons (Tours)

```css
.btn-container {
  display: flex;
  justify-content: center;
}
.filter-btn {
  background: transparent;
  border: 2px solid var(--clr-gold);
  color: var(--clr-gold);
}
.filter-btn:hover {
  background: var(--clr-gold);
  color: var(--clr-white);
}
```

✅ Gold-themed filter buttons that let users select region: north, south, etc.

---

### ⬆️ 9. Back to Top Button

```css
.top-link {
  position: fixed;
  bottom: 3rem;
  right: 3rem;
  background: var(--clr-secondary);
  width: 2rem;
  height: 2rem;
  display: grid;
  place-items: center;
  border-radius: var(--radius);
  visibility: hidden;
}
.show-link {
  visibility: visible;
}
```

✅ Only appears when scrolling down 500px  
✅ Has a bounce animation using:

```css
@keyframes bounce {
  0% { transform: scale(1); }
  50% { transform: scale(1.5); }
  100% { transform: scale(1); }
}
```