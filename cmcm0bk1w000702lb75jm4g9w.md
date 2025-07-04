---
title: "[01] - 03 - Understanding index.html 📝"
datePublished: Fri Mar 21 2025 21:00:00 GMT+0000 (Coordinated Universal Time)
cuid: cmcm0bk1w000702lb75jm4g9w
slug: 03-understanding-indexhtml
tags: html

---

The `index.html` file is the main webpage structure for the Quran Page Viewer app. It sets up the page elements and connects all the styles and scripts that make the app interactive and visually appealing.

### Key Parts

* **DOCTYPE & Language**
    
    ```html
    <!DOCTYPE html>
    <html lang="ar">
    ```
    
    Defines the document as an HTML5 page and sets the language to Arabic (`lang="ar"`) for proper text direction and accessibility.
    
* **Meta Tags**
    
    ```html
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    ```
    
    Ensures proper character encoding (UTF-8) and makes the page responsive on different screen sizes.
    
* **Title & Stylesheet**
    
    ```html
    <title>Quran Page Viewer</title>
    <link rel="stylesheet" href="styles.css" />
    ```
    
    Sets the page title shown in the browser tab and links to the CSS file for styling.
    
* **Main Content Container**
    
    ```html
    <div class="container">
      <h1>📖 Quran 📖</h1>
    
      <div class="pagination">
        <button id="prev" disabled>⬅️ Previous</button>
        <span id="page-number">Page 1</span>
        <button id="next">Next ➡️</button>
      </div>
      <div class="page-input">
        <input type="number" id="page-input" min="1" max="604" placeholder="Page" />
        <button id="jump-btn">Go</button>
      </div>
      <div id="surah-title"></div>
      <div id="surah-details"></div>
    
      <div id="page-content">Loading...</div>
    </div>
    ```
    
    This section includes:
    
    * A heading with Quran emojis for a friendly feel.
        
    * Navigation buttons (`Previous` and `Next`) with a current page number display.
        
    * An input field to jump to a specific page and a “Go” button.
        
    * Containers for Surah title, Surah details, and the actual Quran page content.
        
* **JavaScript Files**
    
    ```html
    <script src="js/model.js"></script>
    <script src="js/view.js"></script>
    <script src="js/controller.js"></script>
    <script src="js/script.js"></script>
    ```
    
    These scripts implement the app logic following the MVC pattern:
    
    * `model.js` fetches data from the Quran API.
        
    * `view.js` updates the UI elements.
        
    * `controller.js` manages the app flow and user interactions.
        
    * `script.js` sets up event listeners and initializes the app.
        

---

### Summary

The `index.html` file provides the structure and entry point for the Quran Page Viewer, linking styles and scripts that work together to deliver a smooth, interactive experience for exploring the Quran page by page.