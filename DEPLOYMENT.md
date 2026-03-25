# 🚀 Woofy Crafts — Deployment Guide

This site is a **static single-file website** (`index.html`). It requires no server, no database, and no build step. It can be deployed for free on multiple platforms in minutes.

---

## ✅ Pre-Deployment Checklist

Before deploying, make sure you have:

- [ ] Updated all product images with real, hosted URLs (not `localhost` paths)
- [ ] Set your WhatsApp number in `wa.me/` links
- [ ] Updated the meta `og:url` and `og:image` tags with your final domain
- [ ] Tested the site locally in Chrome, Firefox, and Safari
- [ ] Tested on a real mobile device or using browser DevTools mobile emulation

---

## 🌐 Option 1 — GitHub Pages (Recommended & Free)

GitHub Pages serves your repo's files directly as a website.

### Steps:

1. **Push your repo to GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/woofy-crafts.git
   git push -u origin main
   ```

2. **Enable GitHub Pages**
   - Go to your repo on GitHub
   - Click **Settings** → **Pages** (left sidebar)
   - Under **Source**, select: `Deploy from a branch`
   - Branch: `main` | Folder: `/ (root)`
   - Click **Save**

3. **Your site will be live at:**
   ```
   https://YOUR_USERNAME.github.io/woofy-crafts/
   ```

4. *(Optional)* **Add a custom domain**
   - Buy a domain from Namecheap, GoDaddy, or Google Domains
   - In GitHub Pages settings, enter your domain under **Custom domain**
   - Add a `CNAME` DNS record pointing to `YOUR_USERNAME.github.io`

---

## ⚡ Option 2 — Netlify (Drag & Drop, Free)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag and drop your entire `woofy-crafts/` folder onto the page
3. Netlify instantly deploys it and gives you a URL like:
   ```
   https://random-name-123.netlify.app
   ```
4. *(Optional)* Rename the site and add a custom domain in Netlify settings

**For continuous deployment from GitHub:**
1. Log in to Netlify → **Add new site** → **Import from Git**
2. Connect your GitHub repo
3. Build command: *(leave blank)*
4. Publish directory: `.` (or leave blank)
5. Click **Deploy site**

Every push to `main` will automatically redeploy the site.

---

## ▲ Option 3 — Vercel (Free)

1. Install the Vercel CLI:
   ```bash
   npm install -g vercel
   ```
2. Run from your project folder:
   ```bash
   vercel
   ```
3. Follow the prompts. Your site will be live at:
   ```
   https://woofy-crafts.vercel.app
   ```

Or connect via the [Vercel dashboard](https://vercel.com/new) by importing your GitHub repo.

---

## ☁️ Option 4 — Cloudflare Pages (Free, Fast CDN)

1. Go to [pages.cloudflare.com](https://pages.cloudflare.com)
2. Click **Create a project** → **Connect to Git**
3. Select your GitHub repo
4. Settings:
   - Framework preset: **None**
   - Build command: *(leave blank)*
   - Build output directory: `/` (root)
5. Click **Save and Deploy**

Your site is deployed on Cloudflare's global CDN for very fast load times worldwide.

---

## 📦 Option 5 — Traditional Web Hosting / cPanel

If you have shared hosting (e.g. HostGator, Bluehost, SiteGround):

1. Log into your hosting **cPanel**
2. Open **File Manager**
3. Navigate to `public_html/`
4. Upload your `index.html` (and any asset folders)
5. Your site is live at your domain immediately

Or use FTP with FileZilla:
```
Host:     ftp.yourdomain.com
Username: your_cpanel_username
Password: your_cpanel_password
Port:     21
```
Upload `index.html` to `public_html/`.

---

## 🔒 HTTPS / SSL

| Platform | HTTPS |
|---|---|
| GitHub Pages | ✅ Auto (Let's Encrypt) |
| Netlify | ✅ Auto |
| Vercel | ✅ Auto |
| Cloudflare Pages | ✅ Auto |
| cPanel hosting | ✅ Usually included — enable in SSL/TLS settings |

All platforms above provide free SSL. Always ensure your site is served over `https://`.

---

## 🔄 Updating the Live Site

### GitHub Pages / Netlify / Vercel / Cloudflare (Git-connected):
```bash
# Make your changes to index.html
git add .
git commit -m "Update: product prices and announcement bar"
git push origin main
```
The site redeploys automatically within ~30 seconds.

### Netlify Drop:
Re-drag the updated folder onto the Netlify drop page — it will update the existing site.

### cPanel / FTP:
Re-upload the updated `index.html` via File Manager or FileZilla, overwriting the old file.

---

## 🛠️ Troubleshooting

| Issue | Fix |
|---|---|
| Images not loading | Use absolute URLs (`https://...`) not relative paths for external images |
| Fonts not loading | Check internet connectivity; Google Fonts requires network access |
| WhatsApp link not working | Ensure number format is `94XXXXXXXXX` (no spaces, no `+`) |
| Site shows old version | Hard refresh: `Ctrl + Shift + R` (Windows) / `Cmd + Shift + R` (Mac) |
| Form not submitting | Wire up to Formspree or EmailJS — see [`CUSTOMIZATION.md`](CUSTOMIZATION.md) |

---

## 📊 Performance Tips

- Compress and resize product images to under 200 KB before uploading
- Use [WebP format](https://squoosh.app) for images for ~30% smaller file sizes
- Enable **Cloudflare** (free plan) in front of any host for global CDN caching
- Run the site through [PageSpeed Insights](https://pagespeed.web.dev) after deployment
