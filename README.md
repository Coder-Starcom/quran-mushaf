# 📖 Quran Page Viewer

A lightweight, interactive web application that lets users browse through the pages of the Quran using an intuitive interface. It uses the [AlQuran Cloud API](https://alquran.cloud/api) to fetch authenticated Quranic data in Uthmani script, complete with Surah details, Juz, Hizb information, and Ayah breakdowns.

---

## 🌐 Live Demo

> <a href="https://quran-mushaf.netlify.app" target="_blank">👉 Quran Page Viewer is Live!</a>
> Browse the Quran page by page with Surah details, Ayah markers, and elegant styling.

---

## 📁 Project Structure

```plaintext
.
├── index.html             # Main HTML page
├── styles.css             # Styling for layout, colors, fonts
├── js/
│   ├── model.js           # Data layer: API calls to fetch Quran & Surah data
│   ├── view.js            # Presentation logic: rendering and DOM updates
│   ├── controller.js      # Logic layer: manages flow between model and view
│   └── script.js          # App bootstrap: connects controller and view
```

---

## 🚀 Features

- 📜 **Page-by-Page Navigation** (1–604)
- 🔢 **Jump to Specific Page**
- 🕌 **Displays Surah Name, Type, Translation, Total Ayahs**
- 🧭 **Displays Juz and Hizb Info**
- 🌙 **Uthmani Script Styling**
- ⚡ **Loads Data Dynamically from Quran API**
- 🎨 **Responsive & Elegant UI**
- 💡 **Highlight for Ruku Marker (۞)**

---

## 🧰 Tech Stack

| Technology                               | Purpose                                     |
| ---------------------------------------- | ------------------------------------------- |
| HTML5 / CSS3                             | Markup & styling                            |
| JavaScript                               | Application logic                           |
| [AlQuran API](https://alquran.cloud/api) | Fetching Quran & Surah data                 |
| Google Fonts                             | Arabic & Latin fonts (`IBM Plex`, `Roboto`) |

---

## 🔧 How It Works

### 📦 Model (`model.js`)

- Fetches Quranic page data using:

  - `https://api.alquran.cloud/v1/page/{page}/quran-uthmani`

- Fetches Surah details using:

  - `https://api.alquran.cloud/v1/surah/{surahNumber}`

### 🖼️ View (`view.js`)

- Manages DOM elements: updates content, navigation, and metadata display
- Renders Ayahs with Uthmani script and custom styling
- Displays Surah details in a responsive table

### 🧠 Controller (`controller.js`)

- Coordinates data from the model and passes it to the view
- Handles logic like inserting the "Bismillah", Surah transitions, and formatting

### 🎬 Entry Script (`script.js`)

- Initializes view and controller
- Attaches event listeners to navigation buttons and jump input

---

## 🎨 UI/UX Highlights

- **Dark theme** with golden typography for readability
- Responsive layout for mobile and tablets
- Custom Arabic font for authenticity
- Automatically hides disabled buttons (e.g., on first/last page)

---

## 🌍 API Reference

Data is fetched from the **AlQuran Cloud API**:

- Page Data: `GET /v1/page/{page}/quran-uthmani`
- Surah Info: `GET /v1/surah/{surahNumber}`

Documentation: [https://alquran.cloud/api](https://alquran.cloud/api)

---

## 🙏 Acknowledgments

- **AlQuran Cloud** for providing a rich and structured Quran API
- Google Fonts team for beautiful Arabic typography
- Inspiration from Quran web viewers and Islamic UI design principles

---

## ✍️ Author

## **Mohammad Saad Ansari**
