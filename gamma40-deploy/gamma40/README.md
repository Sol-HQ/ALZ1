# GAMMA40 — 40Hz Gamma Neural Therapy

A web-based 40Hz gamma light & sound therapy app based on MIT Picower Institute GENUS research.

## Quick Start (Local)

Just open `index.html` in any modern browser. No server required.

```bash
open index.html         # macOS
start index.html        # Windows
xdg-open index.html     # Linux
```

Or use a local dev server (avoids some AudioContext restrictions):

```bash
npx serve .
# → http://localhost:3000
```

---

## Deploy Options

### Option 1 — Netlify (Recommended, Free)

**Drag & Drop (no CLI needed):**
1. Go to https://app.netlify.com/drop
2. Drag this entire `gamma40/` folder onto the page
3. Done — live URL in ~10 seconds

**CLI Deploy:**
```bash
npm install -g netlify-cli
netlify deploy --dir . --prod
```

The included `_redirects` file handles routing automatically.

---

### Option 2 — Vercel (Free)

```bash
npm install -g vercel
cd gamma40
vercel --prod
```

The included `vercel.json` configures routing and sets required COOP/COEP headers
(needed for SharedArrayBuffer / AudioWorklet features).

Or deploy via the Vercel dashboard:
1. Push this folder to a GitHub repo
2. Import repo at https://vercel.com/new
3. Framework preset: **Other** — leave all defaults
4. Deploy

---

### Option 3 — GitHub Pages (Free)

```bash
# Create a new GitHub repo, then:
git init
git add .
git commit -m "Initial GAMMA40 deploy"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/gamma40.git
git push -u origin main
```

Then in GitHub → Settings → Pages → Source: **Deploy from branch** → `main` / `/ (root)`.

The `.nojekyll` file is included so GitHub Pages processes all files correctly.

Live at: `https://YOUR_USERNAME.github.io/gamma40/`

---

### Option 4 — Cloudflare Pages (Free, Fast CDN)

```bash
npm install -g wrangler
wrangler pages deploy . --project-name gamma40
```

Or connect your GitHub repo at https://pages.cloudflare.com

---

### Option 5 — Self-Hosted (Nginx / Apache)

**Nginx config snippet:**
```nginx
server {
    listen 80;
    server_name yourdomain.com;
    root /var/www/gamma40;
    index index.html;

    # Required for Web Audio API
    add_header Cross-Origin-Opener-Policy "same-origin";
    add_header Cross-Origin-Embedder-Policy "require-corp";

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

Copy files: `scp -r gamma40/ user@yourserver:/var/www/gamma40`

---

## Browser Compatibility

| Browser | Audio | Visual Flicker | Notes |
|---------|-------|----------------|-------|
| Chrome 90+ | ✅ | ✅ | Best experience |
| Firefox 88+ | ✅ | ✅ | Full support |
| Safari 14.1+ | ✅ | ✅ | Requires user gesture to start audio (handled) |
| Edge 90+ | ✅ | ✅ | Chromium-based, full support |
| Mobile Chrome | ✅ | ✅ | Keep screen on during session |
| Mobile Safari | ✅ | ✅ | Silent mode must be OFF |

---

## Audio Best Practices

- **Binaural mode** requires stereo headphones
- Keep volume at a comfortable level — around 50–65%
- For **monaural/isochronic** modes, speakers work fine
- Carrier frequency of **400–440Hz** is the sweet spot per clinical literature

## ⚠️ Medical Disclaimer

This app is for educational and wellness purposes only. Not a medical device.
Do NOT use the visual flicker mode if you have epilepsy or photosensitive conditions.
Consult a physician before use if you have any neurological conditions.

---

Built on: MIT Picower Institute GENUS Protocol | Iaccarino et al. Nature 2016 | PMC9714926
