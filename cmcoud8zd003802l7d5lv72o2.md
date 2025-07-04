---
title: "[02] - 02 - Key Features & How They Work 🚀"
datePublished: Thu May 29 2025 21:00:00 GMT+0000 (Coordinated Universal Time)
cuid: cmcoud8zd003802l7d5lv72o2
slug: 02-02-key-features-and-how-they-work
tags: features

---

### 1\. 🗓️ **Dynamic Year in Footer**

The footer automatically updates to show the current year using JavaScript.

#### ✅ Why it matters:

* Keeps the site always up-to-date
    
* Shows attention to detail
    

#### 💡 Code Snippet:

```js
const date = document.getElementById('date');
date.innerHTML = new Date().getFullYear();
```

---

### 2\. 🍔 **Responsive Navigation Toggle**

A hamburger icon toggles the mobile nav menu. Instead of simply showing/hiding, we dynamically calculate height for smooth animation.

#### ✅ Why it matters:

* Fully responsive
    
* Prevents hardcoded height issues
    

#### 💡 Code Snippet:

```js
navToggle.addEventListener('click', function(){
  const contHeight = lCont.getBoundingClientRect().height;
  const linksHeight = links.getBoundingClientRect().height;

  if(contHeight === 0){
      lCont.style.height = `${linksHeight}px`;
  } else {
      lCont.style.height = 0;
  }
});
```

---

### 3\. 📌 **Sticky Navbar on Scroll**

The navbar becomes fixed to the top once the user scrolls past its original height.

#### ✅ Why it matters:

* Enhances navigation usability
    
* Keeps menu accessible on long pages
    

#### 💡 Code Snippet:

```js
window.addEventListener('scroll', function(){
  const scrollHeight = window.pageYOffset;
  const navHeight = navbar.getBoundingClientRect().height;

  if(scrollHeight > navHeight){
      navbar.classList.add('fixed-nav');
  } else {
      navbar.classList.remove('fixed-nav');
  }
});
```

---

### 4\. ⬆️ **"Back to Top" Button**

A floating button appears after scrolling down and links smoothly back to the top.

#### ✅ Why it matters:

* Improves user experience
    
* Adds interactivity and polish
    

#### 💡 Code Snippet:

```js
if(scrollHeight > 500){
  topLink.classList.add('show-link');
} else {
  topLink.classList.remove('show-link');
}
```

```html
<a href="#home" class="scroll-link top-link">
  <i class="fas fa-arrow-up"></i>
</a>
```

---

### 5\. 🎯 **Smooth Scroll Behavior**

All internal navigation links scroll smoothly to their target sections, adjusting for fixed nav height.

#### ✅ Why it matters:

* Smooth experience
    
* Professional feel
    

#### 💡 Code Snippet:

```js
link.addEventListener('click', function(e){
  e.preventDefault();
  const id = e.currentTarget.getAttribute('href').slice(1);
  const element = document.getElementById(id);

  const navHeight = navbar.getBoundingClientRect().height;
  const contHeight = lCont.getBoundingClientRect().height;
  const fixedNav = navbar.classList.contains('fixed-nav');

  let position = element.offsetTop - navHeight;

  if(!fixedNav){
    position -= navHeight;
  }
  if(navHeight > 82){
    position += contHeight;
  }

  window.scrollTo({ top: position, left: 0 });
  lCont.style.height = 0;
});
```

---

### 6\. 🧭 **Filterable Destination Cards (Dynamic Menu)**

Tourist places are rendered from a `menu[]` array and filtered by region using category buttons.

#### ✅ Why it matters:

* Dynamic rendering with JavaScript
    
* Shows basic data-driven UI techniques
    

#### 💡 JavaScript:

```js
function diplayMenuItems(menuItems){
  let displayMenu = menuItems.map(item => {
    return `<article class="menu-item">
      <img src=${item.img} alt=${item.title} class="photo" />
      <div class="item-info">
        <h4>${item.title}</h4>
        <p class="item-text">${item.desc}</p>
      </div>
    </article>`;
  }).join('');
  sectionCenter.innerHTML = displayMenu;
}
```

#### 💡 Dynamic Buttons:

```js
function displayMenuButtons(){
  const categories = menu.reduce((values, item) => {
    if(!values.includes(item.category)){
      values.push(item.category);
    }
    return values;
  }, ['all']);

  const categoryBtns = categories.map(category => {
    return `<button class="filter-btn" type="button" data-id=${category}>
      ${category}
    </button>`;
  }).join('');

  btnContainer.innerHTML = categoryBtns;
}
```

---

### 7\. 🖼️ **Responsive Grid for Tour Cards**

Tour places are displayed in a mobile-first grid using CSS Grid, adapting to wider screens with `@media`.

#### ✅ Why it matters:

* Flexible layout
    
* Modern responsive design
    

#### 💡 CSS:

```css
.section-center {
  display: grid;
  gap: 3rem 2rem;
  justify-items: center;
}
@media screen and (min-width: 1200px) {
  .section-center {
    grid-template-columns: 1fr 1fr;
  }
}
```