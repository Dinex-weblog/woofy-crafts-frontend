# 🎨 Woofy Crafts — Customisation Guide

Everything you need to personalise the site is inside `index.html`. This guide walks through each area step by step.

---

## 1. Brand Colours

Open `index.html` and find the `:root` block near the top of the `<style>` tag. Change any value to update the entire site's colour scheme.

```css
:root {
  --c-wine:   #8B1A4A;  /* Primary — navbars, headings, buttons */
  --c-blush:  #F5A0B8;  /* Accent — highlights, hover states    */
  --c-cream:  #FDF7F0;  /* Background — light sections          */
  --c-gold:   #C9960C;  /* Stars, premium accents               */
  --c-ink:    #1A0A12;  /* Body text                            */
}
```

> 💡 Use a tool like [coolors.co](https://coolors.co) to generate a matching palette.

---

## 2. Logo

Find the logo `<img>` tag inside the navbar:

```html
<img id="nav-logo-img" src="YOUR_LOGO_URL_HERE" alt="Woofy Crafts">
```

Replace `YOUR_LOGO_URL_HERE` with:
- A relative path to your logo file: `src="assets/logo.png"`
- Or a hosted image URL: `src="https://yourdomain.com/logo.png"`

---

## 3. Announcement Bar Text

Find `#announce-track` and edit the `<span>` text inside:

```html
<div class="announce-track" id="announce-track">
  <span>🌸 Free delivery on orders over Rs. 2,500 &nbsp;·&nbsp; ...</span>
  <span>🌸 Free delivery on orders over Rs. 2,500 &nbsp;·&nbsp; ...</span>
</div>
```

> Keep two identical `<span>` elements — the duplicate creates the seamless loop animation.

---

## 4. Products Catalogue

Find the `PRODUCTS` array in the `<script>` section. Each product follows this structure:

```js
{
  id: 1,
  name: "Eternal Rose Bouquet",
  desc: "A timeless arrangement of handcrafted roses.",
  price: 3500,
  category: "bridal",          // bridal | anniversary | birthday | graduation | valentine | friendship | sympathy
  featured: true,              // shows in featured/highlighted spots
  badge: "Best Seller",        // optional badge text, or "" for none
  img: "https://link-to-image.jpg"
}
```

**To add a product:** Copy an existing object, paste it at the end of the array, and update the fields.

**To remove a product:** Delete its object from the array.

**To change price:** Update the `price` value (stored in Sri Lankan Rupees by default).

---

## 5. Customer Reviews

Find the `REVIEWS` array in the `<script>` section:

```js
{
  name: "Nimasha Perera",
  rating: 5,             // 1–5 stars
  text: "Absolutely stunning bouquet! Exceeded all my expectations.",
  date: "March 2025"
}
```

Add, edit, or remove objects as needed.

---

## 6. WhatsApp Number

Search for `wa.me/` in `index.html` and replace the number:

```html
href="https://wa.me/94XXXXXXXXX?text=..."
```

Format: `94` (Sri Lanka country code) + your 9-digit number without the leading `0`.

Example: `078 613 3943` → `https://wa.me/94786133943`

---

## 7. WhatsApp Quick Reply Messages

Find the quick-reply buttons inside the WhatsApp panel:

```html
<button class="wa-quick" data-msg="I'd like to place a custom order 🌸">
  Custom Order
</button>
```

Edit `data-msg` to change what is sent when the user clicks that button.

---

## 8. Social Media Links

Find the footer or contact section and update the `<a href="...">` tags:

```html
<a href="https://instagram.com/woofycrafts_hasii">Instagram</a>
<a href="https://facebook.com/YOUR_PAGE">Facebook</a>
```

---

## 9. Custom Order Form — Submission

By default the form logs data to the console. To wire it up to a real service:

**Option A — Formspree (easiest, free):**
1. Sign up at [formspree.io](https://formspree.io)
2. Create a form and copy your endpoint URL
3. Find the `submitCustomForm()` function and replace the `fetch` URL:

```js
const response = await fetch('https://formspree.io/f/YOUR_FORM_ID', {
  method: 'POST',
  body: JSON.stringify(formData),
  headers: { 'Content-Type': 'application/json' }
});
```

**Option B — EmailJS:**
Follow the [EmailJS docs](https://www.emailjs.com/docs/) and call `emailjs.send()` inside the form handler.

---

## 10. Instagram Gallery Images

Find the `#gallery` section and update the `<img src="...">` tags with your own Instagram photo URLs or local image paths.

---

## 11. Policy Text

Each policy is in its own modal. Search for the modal IDs to find and edit the content:

| Policy | Modal ID |
|---|---|
| Shipping | `#shipping-modal` |
| Returns | `#returns-modal` |
| Privacy | `#privacy-modal` |

Edit the `<p>` and `<h3>` tags inside each modal.

---

## 12. SEO & Meta Tags

Find the `<head>` section and update:

```html
<title>Woofy Crafts | Handcrafted Blooms, Heartfelt Moments</title>
<meta name="description" content="Your description here (150–160 chars)">
<meta property="og:title" content="Woofy Crafts">
<meta property="og:image" content="https://your-image-url.jpg">
<meta property="og:url" content="https://your-domain.com">
```

---

## 13. Currency Symbol

The site displays prices in **Rs.** (Sri Lankan Rupees). To change the currency symbol, search for `Rs.` in `index.html` and replace all instances with your preferred symbol (e.g. `$`, `€`, `£`).

---

## 14. Fonts

The site uses Google Fonts. Find the `<link>` in `<head>`:

```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;1,400&family=Jost:wght@300;400;500;600&display=swap" rel="stylesheet">
```

Replace the font names with any Google Font of your choice and update the CSS `font-family` references accordingly.
