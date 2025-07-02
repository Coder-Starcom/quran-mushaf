---
title: "05 - Understanding the JavaScript Files 🧠📜"
datePublished: Fri Apr 04 2025 21:00:00 GMT+0000 (Coordinated Universal Time)
cuid: cmcm0q7wz000y02l7hu4h0rg4
slug: 05-understanding-the-javascript-files
tags: mvc, js

---

The Quran Page Viewer is powered by four JavaScript files that follow the **MVC (Model-View-Controller)** architecture. Let’s break them down one by one to see how they each contribute to the project.

---

### 1\. `model.js` – The Data Layer 📡

This file is the **Model** in MVC. It handles **data fetching** from external APIs and supplies that data to the rest of the app.

#### Responsibilities:

* Fetch Quranic **page data**.
    
* Fetch **Surah details** (like name, number of verses, type, etc.).
    
* Handle any API errors gracefully.
    

#### Example:

```javascript
const QuranModel = {
  async fetchPageData(page) {
    const response = await fetch(
      `https://api.alquran.cloud/v1/page/${page}/quran-uthmani`
    );
    const data = await response.json();
    return data.data.ayahs;
  },

  async fetchSurahDetails(surahNumber) {
    const response = await fetch(
      `https://api.alquran.cloud/v1/surah/${surahNumber}`
    );
    const data = await response.json();
    return data.data;
  }
};
```

✅ *It keeps all data operations in one place, making the app modular and clean.*

---

### 2\. `view.js` – The Display Layer 👁️

This is the **View** in MVC. It manages **everything the user sees** on the screen and updates the DOM based on the data it receives.

#### Responsibilities:

* Show the Quran text, page number, Surah details, etc.
    
* Enable navigation (next/previous page, jump to page).
    
* Handle UI logic like enabling/disabling buttons and updating layout.
    

#### Example:

```javascript
async updatePage() {
  const content = await QuranController.getQuranPageData(this.currentPage);
  this.pageContent.innerHTML = content;
  this.pageNumberElement.textContent = `Page ${this.currentPage}`;
}
```

✅ *It separates the UI from the logic — making the code easy to maintain and scale.*

---

### 3\. `controller.js` – The Brain of the App 🧠

This file serves as the **Controller** — it connects the Model and View. It decides **what to show and when**, based on user input and app state.

#### Responsibilities:

* Fetch data using the Model.
    
* Pass that data to the View for display.
    
* Handle logic for showing Bismillah, styling Ruku markers, and managing Surah transitions.
    

#### Example:

```javascript
async getQuranPageData(page) {
  const ayahs = await QuranModel.fetchPageData(page);
  for (const ayah of ayahs) {
    if (ayah.surah.number !== lastSurah) {
      const surahDetails = await QuranModel.fetchSurahDetails(ayah.surah.number);
      QuranView.displaySurahDetails(surahDetails, juz, hizb);
    }
    // Render each Ayah here...
  }
}
```

✅ *It ensures the app runs smoothly by managing the flow between the data and the interface.*

---

### 4\. `script.js` – The App Starter 🔁

This is the **entry point** of the application. It initializes everything when the page loads.

#### Responsibilities:

* Set up the View and Controller.
    
* Add event listeners for buttons like "Next", "Previous", and "Go".
    

#### Example:

```javascript
document.addEventListener("DOMContentLoaded", () => {
  QuranController.init(QuranView);
  QuranView.init();

  document.getElementById("prev").addEventListener("click", () => QuranView.changePage(-1));
  document.getElementById("next").addEventListener("click", () => QuranView.changePage(1));
  document.getElementById("jump-btn").addEventListener("click", () => QuranView.jumpToPage());
});
```

✅ *It connects the dots when the app loads, setting the foundation for user interaction.*

---

## Summary 🧩

Each JavaScript file plays a focused role in making the Quran Page Viewer functional and cleanly structured:

| File | Role in MVC | Responsibility |
| --- | --- | --- |
| `model.js` | Model | Fetch Quranic data from the API |
| `view.js` | View | Render the UI and update DOM |
| `controller.js` | Controller | Coordinate between View and Model |
| `script.js` | Entry Point | Initialize app and handle user events |

Together, they form a maintainable and scalable app structure powered by vanilla JavaScript — no frameworks required.