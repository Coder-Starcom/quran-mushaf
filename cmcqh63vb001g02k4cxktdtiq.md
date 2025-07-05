---
title: "[02] - 05 - Understanding app.js"
datePublished: Wed Sep 04 2024 21:00:00 GMT+0000 (Coordinated Universal Time)
cuid: cmcqh63vb001g02k4cxktdtiq
slug: 02-05-understanding-appjs
tags: js

---

### 📅 1. Set Dynamic Footer Year

```js
const date = document.getElementById('date');
date.innerHTML = new Date().getFullYear();
```

✅ This grabs the current year and inserts it into the `<span id="date">` in the footer so it's always up-to-date.

---

### 🍔 2. Navbar Toggle (Mobile Menu)

```js
const navToggle = document.querySelector('.nav-toggle');
const lCont = document.querySelector('.links-container');
const links = document.querySelector('.links');
```

These elements reference the **hamburger icon**, the **container** that hides/shows links, and the actual **navigation list**.

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

✅ On clicking the menu icon:

* If the menu is closed, it slides open (by setting height)
    
* If it's open, it collapses back to height `0`
    

This approach avoids toggling `display: none` and allows smooth transitions.

---

### 📌 3. Sticky Navbar + Show "Back to Top" Button

```js
const navbar = document.getElementById('nav');
const topLink = document.querySelector('.top-link');

window.addEventListener('scroll', function(){
    const scrollHeight = window.pageYOffset;
    const navHeight = navbar.getBoundingClientRect().height;

    if(scrollHeight > navHeight){
        navbar.classList.add('fixed-nav');
    } else {
        navbar.classList.remove('fixed-nav');
    }

    if(scrollHeight > 500){
        topLink.classList.add('show-link');
    } else {
        topLink.classList.remove('show-link');
    }
});
```

✅ Adds/removes classes based on how far you've scrolled:

* `fixed-nav`: makes navbar sticky
    
* `show-link`: makes "back to top" arrow visible
    

---

### ⛵ 4. Smooth Scrolling to Sections

```js
const scrollLinks = document.querySelectorAll('.scroll-link');

scrollLinks.forEach(function(link){
    link.addEventListener('click', function(e){
        e.preventDefault();
        const id = e.currentTarget.getAttribute('href').slice(1);
        const element = document.getElementById(id);

        const navHeight = navbar.getBoundingClientRect().height;
        const contHeight = lCont.getBoundingClientRect().height;
        const fixedNav = navbar.classList.contains('fixed-nav');

        let position = element.offsetTop - navHeight;

        if(!fixedNav){
            position = position - navHeight;
        }
        if(navHeight > 82){
            position = position + contHeight;
        }

        window.scrollTo({
            left:0,
            top:position,
        });
        lCont.style.height = 0;
    });
});
```

✅ Enables **smooth scrolling** to target sections when links are clicked:

* Corrects for navbar height
    
* Ensures precise scroll even if navbar isn’t fixed
    
* Collapses mobile menu afterward
    

---

### 🧭 5. Tour Data (Array of Places)

```js
const menu = [ {...}, {...}, {...} ];
```

✅ The `menu` array contains 20+ destinations. Each object has:

* `id`, `title`, `img`, `category`, and `desc`
    

```js
{
  id: 1,
  title: "Agra",
  img: "./images/01.png",
  category: "north",
  desc: `The Taj Mahal...`
}
```

These objects will be dynamically rendered on the Tours page.

---

### 🧱 6. DOM Targets for Rendering

```js
const sectionCenter = document.querySelector(".section-center");
const btnContainer = document.querySelector(".btn-container");
```

✅ These are the containers where:

* **Tours** will be inserted
    
* **Filter buttons** (north/south/west/east/all) will appear
    

---

### 🚀 7. Initialize the Page on Load

```js
window.addEventListener("DOMContentLoaded", function () {
  diplayMenuItems(menu);
  displayMenuButtons();
});
```

✅ When the page loads:

* All tour items are shown
    
* Filter buttons are created
    

---

### 🎨 8. Display Tours

```js
function diplayMenuItems(menuItems){
  let displayMenu = menuItems.map(function (item) {
    return `<article class="menu-item">
          <img src=${item.img} alt=${item.title} class="photo" />
          <div class="item-info">
              <h4>${item.title}</h4>
            <p class="item-text">${item.desc}</p>
          </div>
        </article>`;
  });
  displayMenu = displayMenu.join("");
  sectionCenter.innerHTML = displayMenu;
}
```

✅ Loops through each destination and creates:

* An `<article>` block with image, title, and description
    
* Injects it into the `.section-center` container
    

---

### 🧭 9. Filter Buttons (Regions)

```js
function displayMenuButtons(){
  const categories = menu.reduce(function(values,item) {
    if(!values.includes(item.category)){
      values.push(item.category);
    }
    return values;
  }, ['all']);
```

✅ Gathers **unique categories** like `north`, `south`, etc. and adds `all` to the list

```js
  const categoryBtns = categories.map(function(category){
    return `<button class="filter-btn" type="button" data-id=${category}>
        ${category}
      </button>`;
  }).join("");
```

✅ Creates buttons dynamically with `data-id="category"` for filtering

```js
  btnContainer.innerHTML = categoryBtns;

  const filterBtns = btnContainer.querySelectorAll(".filter-btn");

  filterBtns.forEach(function (btn) {
    btn.addEventListener("click", function (e) {
      const category = e.currentTarget.dataset.id;
      const menuCategory = menu.filter(function (menuItem) {
        if (menuItem.category === category) {
          return menuItem;
        }
      });
      if (category === "all") {
        diplayMenuItems(menu);
      } else {
        diplayMenuItems(menuCategory);
      }
    });
  });
}
```

✅ Adds click listeners to each filter button:

* If "all", show all items
    
* Otherwise, filter and show only that region’s destinations