---
title: "04 - Understanding styles.css 🎨"
datePublished: Fri Mar 28 2025 21:00:00 GMT+0000 (Coordinated Universal Time)
cuid: cmcm0ldf5000x02l7htby9liq
slug: 04-understanding-stylescss
tags: css

---

The `styles.css` file defines how the Quran Page Viewer looks and feels — from fonts and colors to layout and responsiveness. It ensures that the app is both beautiful and easy to use across devices.

---

### 🔤 Fonts

```css
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Arabic");
@import url("https://fonts.googleapis.com/css2?family=Roboto");
```

---

### 🌐 Global Styles

```css
* {
  font-family: "Roboto", serif;
}
```

Sets a default font for all elements to ensure consistency.

```css
body {
  text-align: center;
  padding: 20px;
  background-color: #0d1117;
  color: #f0e68c;
}
```

* Centers content, applies padding.
    
* Dark background with light golden text for a visually calm experience.
    

---

### 📦 Container Styling

```css
.container {
  max-width: 700px;
  margin: auto;
  padding: 20px;
  background: #1c1f26;
  border-radius: 10px;
  box-shadow: 0 0 15px rgba(255, 215, 0, 0.2);
}
```

Creates a centered content box with a dark background and soft gold glow, giving it a focused and premium feel.

---

### 🔄 Pagination Buttons

```css
button {
  padding: 10px;
  margin: 5px;
  background: #f0e68c;
  color: black;
  border-radius: 5px;
  cursor: pointer;
}
button:disabled {
  background: #555;
  cursor: not-allowed;
  display: none;
}
```

* Stylish, gold-colored buttons with a dark fallback when disabled.
    
* Disabled buttons are hidden to reduce clutter on page edges.
    

---

### 📖 Ayah & Surah Styling

```css
.ayah {
  font-size: 24px;
  line-height: 2;
  font-family: "IBM Plex Sans Arabic", sans-serif;
  display: block;
}
```

* Increases readability for Arabic verses with larger text and proper spacing.
    

```css
.ayah-number {
  color: #ffd700;
  font-weight: bold;
}
```

* Highlights ayah numbers in gold to distinguish them easily.
    

```css
.surah-title,
.bismillah {
  font-size: 22px–28px;
  color: #ffcc00;
  font-weight: bold;
}
```

* Makes the Surah name and Bismillah stand out using a brighter gold and larger text.
    

---

### 🧮 Page Input Area

```css
.page-input {
  margin-top: 15px;
}
```

Adds spacing around the jump-to-page input field for better layout.

---

### 📋 Surah Details Table

```css
table {
  width: 100%;
}
td, th {
  padding: 8px;
  border-left: #ffcc00 solid 1.5px;
  border-right: #ffcc00 solid 1.5px;
  background-color: #ffcc0077;
  text-align: center;
}
```

* Displays Surah metadata (type, name, translation, etc.) in a neat, styled table with golden borders.
    

---

### 📱 Responsive Design

```css
@media screen and (max-width: 768px) {
  table {
    font-size: 14px;
  }
  td, th {
    padding: 5px;
  }
}
```

* Optimizes the table and text for smaller screens (phones/tablets), making it mobile-friendly.
    

---

### 🧭 Directional & Special Markers

```css
#page-content {
  direction: rtl;
}
.ruku-marker {
  color: #ffffff;
  font-size: 30px;
  font-weight: 900;
}
```

* Sets Quranic text to **right-to-left** (RTL), as is standard for Arabic.
    
* Ruku markers (۞) are styled in white and bold to help identify section breaks.
    

---

## Summary ✨

The `styles.css` makes the Quran Page Viewer visually appealing, easy to read, and usable across devices — combining traditional aesthetics with modern responsiveness.