# 👜 Modern Arabic/FR Tailwind Store

A sleek, mobile‑first storefront for women’s shoes & bags, built with **HTML + TailwindCSS + Vanilla JS** and full **RTL/LTR** support (Arabic 🇲🇦 / French 🇫🇷), dark mode, local cart, and WhatsApp ordering.

<p align="center">
  <img src="docs/cover.png" alt="Storefront hero screenshot" width="900"/>
</p>

---

## ✨ Highlights

* **RTL-first** design with instant Arabic ↔ French toggle
* **Dark/Light themes** with localStorage persistence
* **Dynamic catalog** (rendered from JS object)
* **Local mini‑cart** with badges & totals (no backend)
* **Cash on Delivery demo** + **WhatsApp ordering** CTA
* **Filters & quick view** modal (best sellers / shoes / bags)
* **Animated reveals** on scroll
* **Moroccan phone validation** and MAD currency formatting

---

## 📸 Screenshots

> Replace paths with your images under `docs/`.

* Hero & trust bar

  ![Hero](docs/screenshot-hero.png)

* Product grid, filters & quick view

  ![Products](docs/screenshot-products.png)

* Mini‑cart & checkout demo

  ![Cart](docs/screenshot-cart.png)

* Dark mode + FR

  ![Dark](docs/screenshot-dark-fr.png)

---

## 🧱 Tech Stack

* **HTML5** (semantic, responsive)
* **TailwindCSS** via CDN (with `forms` + `container-queries` plugins)
* **Vanilla JavaScript** (no framework)
* **Google Fonts**: Manrope, Noto Sans Arabic
* **Material Symbols** icons

---

## 🚀 Live Demo

Add your deployment link here (GitHub Pages/Vercel/Netlify):

```
https://<your-username>.github.io/<repo>
```

---

## 🔧 Quick Start (Local)

```bash
# 1) Clone
git clone https://github.com/<your-username>/<repo>.git
cd <repo>

# 2) Open the site
# Just open index.html in your browser (no build step required)

# Optional: serve locally for nice URLs
npx serve .   # or: python3 -m http.server 5173
```

> Tailwind is loaded from CDN, so there’s nothing to install.

---

## 🗂️ Project Structure

```
<repo>/
├── index.html          # Main app (HTML + Tailwind + JS)
├── docs/               # README assets (screenshots, cover)
│   ├── cover.png
│   ├── screenshot-hero.png
│   ├── screenshot-products.png
│   ├── screenshot-cart.png
│   └── screenshot-dark-fr.png
└── README.md
```

---

## 🌍 i18n (AR/FR)

* Current language key is stored in `localStorage` and toggled via the **AR/FR** pill.
* Text is mapped using the `i18n` object and `[data-i18n]`/`[data-i18n-ph]` attributes.

```js
// Toggle language
$('#langToggle').addEventListener('click', () => {
  currentLang = currentLang === 'ar' ? 'fr' : 'ar';
  applyI18n(currentLang);
});
```

**RTL/LTR** switches automatically via `document.documentElement.dir`.

---

## 🌓 Theme (Dark/Light)

* Theme state persists in `localStorage`.
* Toggle button swaps the icon and `dark` class on `<html>`.

```js
function applyTheme(theme){
  if(theme==='dark') document.documentElement.classList.add('dark');
  else document.documentElement.classList.remove('dark');
  localStorage.setItem('theme', theme);
}
```

---

## 🛒 Catalog & Cart

Products come from a JS object (`products` + `newProducts`, merged into `allProducts`). Rendering is filter‑aware and currency is formatted to **MAD** based on language locale.

```js
const newProducts = {
  p5: { id:'p5', price:220, ar:{name:'بلغة جلد تقليدية', desc:'راحة أصيلة.'}, fr:{name:'Babouche en cuir', desc:'Confort authentique.'}, img:'<img-url>' },
  // ...
};
```

Cart data is stored in `localStorage` under `cart_v1` with helpers: `add`, `remove`, `count`, `total`, `save`, `load`.

---

## 💬 WhatsApp Ordering

Set your number once and the **CTA** buttons will open a pre‑filled WhatsApp message with cart contents.

```js
const whatsappNumber = '212600000000'; // ← change me
```

* CTA on hero (`#whatsappCTA`)
* Checkout drawer button (`#waOrderBtn`)

---

## ✅ Form Validation (COD / Contact)

* Minimal inline validation with error rings
* **Moroccan phone regex** for 06/07 prefixes: `/^(?:\+?212|0)(?:6|7)\d{8}$/`

---

## 🧩 Features Checklist

* [x] RTL/LTR language toggle (AR/FR)
* [x] Dark mode with persistence
* [x] Product filters (all/shoes/bags/best)
* [x] Quick view modal
* [x] Mini‑cart with totals
* [x] WhatsApp order integration
* [x] Basic COD form validation
* [x] Scroll reveal animations

---

## 🛠️ Customize

* **Branding**: search for `data-i18n="brand"` and footer copy
* **Palette**: Tailwind config (inlined) → `colors.primary`, `colors.secondary`
* **Border radii**: `borderRadius` scale
* **Images**: replace Unsplash/Google image URLs with your assets
* **Catalog**: extend `newProducts` and `productMeta`

---

## 📦 Deploy

**GitHub Pages**

1. Push to `main` with `index.html` at the root
2. Repo → *Settings* → *Pages* → Deploy from branch → `main` / `/ (root)`
3. Your site will be served at: `https://<user>.github.io/<repo>/`

**Vercel/Netlify**

* Import repo → set project → deploy (no build command needed)

---

## 🤝 Contributing

PRs welcome! For major changes, open an issue first to discuss what you’d like to change.

---

## 📄 License

This project is released under the **MIT License**. See [LICENSE](LICENSE) (create if missing).

---

## 🙌 Credits

* Tailwind CSS — [https://tailwindcss.com](https://tailwindcss.com)
* Material Symbols — [https://fonts.google.com/icons](https://fonts.google.com/icons)
* Fonts — Manrope, Noto Sans Arabic

---

## ℹ️ Notes for Reviewers

* This is a **static** site; no backend. Data persists via `localStorage` only.
* Phone validation & currency formatting are tailored to **Morocco** by default.
