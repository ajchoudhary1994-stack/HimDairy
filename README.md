# HimDairy — Pure. Fresh. Himachali.

Website for HimDairy, a direct-to-consumer Himalayan A2 desi cow milk brand offering milk, ghee, paneer, curd, and lassi.

## 📁 Project Structure

```
himdairy-website/
├── index.html          # Full site — HTML, CSS, and JavaScript (single-file build)
├── assets/
│   ├── hero.mp4         # Hero background video
│   └── poster.jpg        # Poster/fallback image for hero video
├── package.json
├── netlify.toml         # Netlify deploy configuration
└── README.md
```

This is a **plain static site** — no build step, no framework. Everything runs directly in the browser.

## 🚀 Run locally

No install required if you have Node.js:

```bash
npx serve .
```

Then open `http://localhost:3000` in your browser.

Or with the npm script:

```bash
npm run dev
```

## 📤 Deploy to GitHub

```bash
git init
git add .
git commit -m "Initial commit — HimDairy website"
git branch -M main
git remote add origin https://github.com/<your-username>/himdairy-website.git
git push -u origin main
```

## 🌐 Deploy to Netlify

**Option A — Connect GitHub repo (recommended)**
1. Push this project to GitHub (steps above).
2. Go to [app.netlify.com](https://app.netlify.com) → **Add new site** → **Import an existing project**.
3. Select your `himdairy-website` repo.
4. Build settings: leave **Build command** empty, set **Publish directory** to `.` (root).
5. Deploy.

**Option B — Drag and drop**
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop).
2. Drag the entire project folder in.

> `netlify.toml` is already configured with the publish directory and cache headers for the video/image assets, so no manual setup is needed either way.

## 📝 Notes

- `hero.mp4` (~11.5 MB) is the largest asset. If you hit Netlify's free-tier bandwidth limits, consider compressing the video (H.264, lower bitrate, ~5–7 MB target) or serving it from a CDN.
- Contact details (phone, WhatsApp, email) are hardcoded in `index.html` — search for `919459755408` and `ajchoudhary1994@gmail.com` if these ever need to change.
