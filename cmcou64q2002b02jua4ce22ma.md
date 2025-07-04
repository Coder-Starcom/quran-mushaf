---
title: "[02] - 01 - Architecture & Tech Stack"
datePublished: Thu May 22 2025 21:00:00 GMT+0000 (Coordinated Universal Time)
cuid: cmcou64q2002b02jua4ce22ma
slug: 02-01-architecture-and-tech-stack
tags: tech-stack, arch

---

### 🧱 **Architecture: MVC-Inspired Structure**

While not a full MVC (Model-View-Controller) framework, this project loosely follows its **principles** to keep the structure modular and clean:

* **Model (Data)** – All tour destinations are stored in a structured JavaScript array (`menu[]`) that represents our "travel database."
    
* **View (UI)** – The layout and components are built in `index.html` and styled using `styles.css` with responsive design in mind.
    
* **Controller (Logic)** – The interactive behavior, such as navbar scroll logic, button filtering, and DOM rendering, is handled in `app.js`.
    

This separation ensures each file has a clear responsibility, making it easier to maintain or expand in the future.

---

### ⚙️ **Tech Stack**

> No frameworks. No dependencies. 100% pure frontend fundamentals. 🌱

| Layer | Tool/Language | Purpose |
| --- | --- | --- |
| 🧩 Structure | **HTML5** | For creating semantic layout and sectioned content (home, about, services, tours) |
| 🎨 Styling | **CSS3** (with Grid, Flexbox, Media Queries) | For layout, responsiveness, and theming (via custom variables) |
| 🧠 Behavior | **Vanilla JavaScript (ES6)** | For DOM manipulation, scroll behavior, navbar control, and filtering logic |
| 💻 Icons | **Font Awesome** | For clean and scalable icons (hamburger menu, arrow-up button) |
| 🔤 Fonts | **Google Fonts** | For a modern and clean UI with `Roboto` and `Open Sans` |
| 🌐 Hosting | *(Optional)* GitHub Pages / Netlify | To easily deploy the static site live |

---

### 🗃️ File Structure (Simplified)

```plaintext
📁 TravelScroll
├── index.html       # main HTML structure
├── styles.css       # custom styles and layout
├── app.js           # all interactive logic and data
└── images/          # all destination images
```

---

This simple yet powerful tech stack was chosen intentionally to **reinforce core frontend concepts** without the complexity of external libraries or frameworks.