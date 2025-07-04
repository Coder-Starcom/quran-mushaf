---
title: "[01] - 01 - Architecture & Tech Stack ⚙️🖥️"
datePublished: Fri Mar 07 2025 21:00:00 GMT+0000 (Coordinated Universal Time)
cuid: cmclzwo2q000402jm0zt1d1r0
slug: 01-01-architecture-and-tech-stack
tags: architecture, tech-stack

---

### What is Architecture? 🏗️

Think of **architecture** as the blueprint or plan of a building — it shows how everything fits together and works. In a web app, architecture is the way different parts of the app are organized and how they communicate with each other to make the whole thing work smoothly.

### What is Tech Stack? 🛠️

A **tech stack** is just the set of tools and technologies used to build a project, like the ingredients in a recipe.

### MVC (Model-View-Controller) Architecture 🏗️

To keep the project clean and maintainable, I used the **MVC design pattern**:

* **Model** 📦: Handles all data fetching and management. It talks to the AlQuran Cloud API to get Quranic text and Surah details.
    
* **View** 👀: Responsible for rendering everything you see — the Quran pages, Surah info, navigation buttons, and handling user inputs.
    
* **Controller** 🎛️: The middleman that connects Model and View. It manages user actions, fetches data from the Model, and updates the View accordingly.
    

This separation makes the code modular, easier to debug, and ready for future improvements.

### Tech Stack 🛠️

* **HTML5** 📄: Structuring the web pages with semantic, accessible markup.
    
* **CSS3** 🎨: Styling the app with responsive design and beautiful Arabic fonts to showcase the Uthmani script elegantly.
    
* **JavaScript (Vanilla)** 💻: Powers the app logic — API calls, dynamic content updates, and user interaction without any heavy frameworks.
    
* **AlQuran Cloud API** 🌐: Provides authentic Quranic text and metadata dynamically.
    
* **Hosting** 🚀: Deployed on Netlify for fast, reliable access worldwide.
    

This stack strikes a perfect balance — lightweight, efficient, and easy to maintain.