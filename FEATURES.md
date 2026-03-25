# 🌸 Woofy Crafts — Feature Documentation

This document describes every major feature built into `index.html` and how each one works.

---

## 🛒 Shopping Cart

- Accessible via the cart icon (🛒) in the navbar or the mobile menu
- Opens as a right-side slide-in drawer (`#cart-drawer`)
- Supports:
  - Adding products with **Add to Cart** buttons
  - Adjusting item quantities with `+` / `−` controls
  - Removing individual items
  - Displaying a **running total** in real time
- Cart item count badge (`#cart-count`) updates dynamically
- Cart state is kept in a JavaScript array in memory (resets on page reload)

---

## 💖 Wishlist

- Accessible via the heart icon in the navbar (`#wishlist-toggle`)
- Opens as a right-side slide-in drawer (`#wishlist-drawer`)
- Each product card has a heart toggle button
- Wishlist count badge (`#wishlist-count`) updates live
- Items can be moved from wishlist directly to cart

---

## 🔍 Search

- Triggered by the search icon in the navbar (`#search-toggle`)
- Opens a full-screen search overlay
- Searches product names and descriptions in real time as the user types
- Results rendered dynamically below the input field
- Closes on `Escape` key or clicking outside the overlay

---

## 🎨 Custom Order Form

Located in `#custom` section. Fields include:

| Field | Type | Description |
|---|---|---|
| Name | Text input | Customer full name |
| Phone | Text input | Contact number (prefilled hint: Sri Lankan format) |
| Bouquet Type | Dropdown | Bridal, Anniversary, Birthday, etc. |
| Budget | Dropdown | Price range tiers |
| Occasion | Dropdown | Wedding, Valentine's, Graduation, etc. |
| Desired Date | Date picker | Delivery or event date |
| Colour Preferences | Visual picker | Swatch-based multi-colour selector |
| Message | Textarea | Heartfelt card message |
| Notes | Textarea | Extra size/detail instructions |

On submission, the form data can be wired to a backend or email service (see [`CUSTOMIZATION.md`](CUSTOMIZATION.md)).

---

## 📱 WhatsApp Chat Panel

- Floating WhatsApp button (bottom-right corner)
- Clicking opens an in-page chat panel styled like WhatsApp
- **Quick reply buttons** send preset messages (e.g. "I'd like to place a custom order")
- User can type a free-form message
- On send, the message is composed into a `wa.me` deep-link and opened in WhatsApp
- A simulated "typing..." indicator appears before redirect

---

## 🌸 Animations & Visual Effects

| Effect | Trigger | Implementation |
|---|---|---|
| Floating petals | Constant background | CSS keyframe animation, JS spawns elements |
| Custom cursor | Mouse movement | `#cursor` + `#cursor-ring` divs follow pointer |
| Click sparkle burst | Click on any `.btn-primary` or `.add-to-cart-btn` | JS creates emoji/star elements at click coords |
| Touch burst | Mobile tap / drag | JS detects `touchstart` / `touchmove` |
| Scroll reveal | Scroll into view | `IntersectionObserver` adds `.visible` class |
| Button ripple | Click on any button | JS injects a `<span>` ripple element |

---

## 📦 Product Grid — Filtering & Sorting

Located in `#products` section.

**Filters** (tag buttons in `#products-filters`):
- All, Bridal, Anniversary, Birthday, Graduation, Valentine's, Friendship, Sympathy

**Sort options** (dropdown `#sort-select`):
- Featured, Price: Low to High, Price: High to Low, Name: A–Z

Products are defined in a JavaScript array `PRODUCTS` and rendered dynamically into `#products-grid`. Each card includes:
- Product image
- Name & short description
- Price
- Add to Cart button
- Wishlist toggle heart

---

## ⭐ Customer Reviews

- Defined in a `REVIEWS` JavaScript array
- Rendered into `#reviews-grid`
- Each card shows: reviewer name, star rating (1–5), review text, and date
- Grid is responsive (1 → 2 → 3 columns)

---

## 🖼️ Instagram Gallery

- Located in `#gallery`
- Showcases a grid of bouquet photos linking to `@woofycrafts_hasii`
- Images are laid out in a CSS masonry-style responsive grid

---

## 📜 Policy Modals

Three policy overlays accessible from `#policies` section and footer links:

| Policy | Trigger ID | Content |
|---|---|---|
| Shipping Policy | `#shipping-modal` | Delivery times, areas, costs |
| Returns Policy | `#returns-modal` | Return window, conditions |
| Privacy Policy | `#privacy-modal` | Data collection, rights, contact |

Modals close on overlay click or close button.

---

## 📣 Announcement Bar

- `#announce-bar` at the very top of the page
- CSS marquee animation scrolls promotional text
- Content defined in `#announce-track` — duplicate spans create a seamless loop
- Bar hides on scroll down, reappears on scroll up (controlled via JS scroll listener)

---

## 🌙 Dark Mode

- Detected via `prefers-color-scheme: dark` CSS media query
- All colours reference CSS custom properties (`--c-*` variables) defined in `:root`
- Dark overrides defined in a `@media (prefers-color-scheme: dark)` block
- No manual toggle needed — respects OS setting automatically

---

## 📲 Responsive / Mobile

- Hamburger menu (`#hamburger`) toggles `#mobile-menu` slide-in panel
- Breakpoints at `768px` and `480px`
- Product grid collapses from 4 → 2 → 1 columns
- Touch-specific events for sparkle animation
- Font sizes and padding scale via CSS clamp / media queries

---

## 🔔 Toast Notifications

- `#toast-container` at top-right of viewport
- Appears when a product is added to cart or wishlist
- Auto-dismisses after ~2.5 seconds
- Stacks if multiple toasts fire in quick succession
