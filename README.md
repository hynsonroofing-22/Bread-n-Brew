# Bread N Brew Café — website

Filipino bakery & café, 236 Onehunga Mall, Onehunga, Auckland 1061 · 09 971 2673

The whole site is **one file**: `index.html`. Photos, the logo and all the fonts-styling are
embedded inside it, so there is no build step, no npm, no framework. Open it in a browser and
it works, offline included.

## Files

| File | What it is |
|---|---|
| `index.html` | The entire website |
| `og.jpg` | Preview image shown when the link is shared on Facebook / Messenger / WhatsApp. Not displayed on the site. |
| `netlify.toml` | Netlify settings — no build command, caching and security headers |
| `robots.txt` | Lets search engines index the site |
| `logo/` | Print-ready logo files (PNG + PDF). Not used by the site; kept here so they live with the project. |

## Deploy to Netlify (GitHub, auto-deploy on every push)

1. Create an **empty** repo on GitHub — https://github.com/new — name it `bread-n-brew`.
   Do **not** tick "Add a README".
2. In this folder, run:

   ```bash
   git remote add origin https://github.com/YOUR-USERNAME/bread-n-brew.git
   git branch -M main
   git push -u origin main
   ```

3. Go to https://app.netlify.com → **Add new site** → **Import an existing project** → GitHub →
   pick `bread-n-brew`.
4. Leave build command **empty** and publish directory as `.` (netlify.toml already sets this).
   Click **Deploy**.
5. **Site configuration → Change site name** → `bread-n-brew` to get
   `bread-n-brew.netlify.app`.

From then on, every `git push` redeploys automatically.

## After the first deploy — one thing to change

`og:image` currently points at the relative path `og.jpg`. Facebook and most link previewers
need an **absolute** URL. Once you know the address, edit `index.html` and replace both
occurrences of `content="og.jpg"` with your real URL:

```html
<meta property="og:image" content="https://bread-n-brew.netlify.app/og.jpg">
<meta name="twitter:image"  content="https://bread-n-brew.netlify.app/og.jpg">
```

Then push again, and test at https://developers.facebook.com/tools/debug/

## Updating the site

Replace `index.html`, then:

```bash
git add -A && git commit -m "Update site" && git push
```

## Custom domain (later)

Netlify → **Domain management** → **Add a domain**. Netlify issues the HTTPS certificate free.
Whoever registers the domain points it at Netlify's nameservers.
