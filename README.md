# HimDairy — Website

Premium, mobile-first ordering website for HimDairy. Pure HTML/CSS/JS — no build step, no dependencies.

## Structure

```
himdairy/
├── index.html        Home page (hero, products, order form, why us, reviews, FAQ, contact)
├── privacy.html       Privacy policy
├── terms.html         Terms of service
├── css/style.css      All styles (design tokens at the top)
├── js/script.js       Product data, cart logic, WhatsApp message builder, form validation, UI interactions
├── netlify.toml        Netlify config (headers, caching, redirects)
├── robots.txt / sitemap.xml   SEO
└── README.md
```

## Run locally

No build tools needed. Either:
- Open `index.html` directly in a browser, or
- From this folder, run `python3 -m http.server 8000` and visit `http://localhost:8000`

## Deploy to Netlify

1. Push this folder to a GitHub repository.
2. In Netlify: **Add new site → Import an existing project → GitHub** → select the repo.
3. Build command: leave blank. Publish directory: `.` (already set in `netlify.toml`).
4. Deploy. Netlify will auto-redeploy on every push to your main branch.

## Deploy to GitHub Pages (alternative)

Push to a repo, then in **Settings → Pages**, set the source to the `main` branch, root folder.

## Things you'll likely want to edit

**Prices, products, WhatsApp number** — all in `js/script.js` at the top:
```js
var WHATSAPP_NUMBER = "919459755408"; // no + or spaces
var PRODUCTS = [ { id: "milk", name: "Fresh Cow Milk", unit: "Litre", price: 65, ... }, ... ];
```
Editing the `PRODUCTS` array is enough — cards, quantity steppers, the order summary and the WhatsApp message all update automatically.

**Colors and fonts** — CSS custom properties at the top of `css/style.css` under `:root`.

**Hero background photo** — the hero currently uses a forest-green gradient with an SVG mountain-ridge illustration (`.hero-ridges` in `style.css` / `index.html`) so the site never depends on an external image link. To use a real farm photo instead, add your image to an `assets/` folder and set it as a background on `.hero` in `css/style.css`, e.g.:
```css
.hero{ background: linear-gradient(180deg, rgba(15,61,46,.85), rgba(10,42,31,.92)), url("../assets/farm-hero.jpg") center/cover; }
```

**Google Map** — in `index.html`, the map `<iframe>` currently points to a generic "Palampur, Kangra, Himachal Pradesh" search. Replace the `src` with your exact pinned farm location (share → embed a map from Google Maps) once you have the precise address.

**Reviews / FAQ copy** — plain HTML in the relevant `<section>` of `index.html`; duplicate a `.review-card` or `.faq-item` block to add more.

## How ordering works

1. Customer sets quantities on product cards (stored in memory, no backend needed).
2. The order summary and mobile sticky bar update live.
3. Customer fills in the order form (name, phone, address, delivery date/time).
4. Tapping **Send Order on WhatsApp** validates the form, builds a formatted order message, and opens `https://wa.me/<number>?text=<order details>` — this hands off to WhatsApp on the customer's own device. No server, database or payment processing is required.

## Notes

- Fully responsive (mobile / tablet / desktop), keyboard accessible, respects `prefers-reduced-motion`.
- No external JS frameworks — fast load, nothing to break.
- SEO: semantic HTML, meta/OG tags, `Store` structured data (JSON-LD), `robots.txt`, `sitemap.xml`. Update the placeholder domain (`himdairy.in`) throughout once your real domain is live.
