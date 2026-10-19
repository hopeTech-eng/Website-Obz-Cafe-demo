# OBZ Cafe Website

A single-page website for OBZ Cafe, 115 Lower Main Road, Observatory, Cape Town. It is one self-contained HTML file with no build step, no framework and no dependencies to install.

## Features

- **Full-screen hero** with a slow-zoom photo, an animated headline and a key-facts strip
- **Interactive menu** with tabs for pizzas, tapas, burgers, salads, nachos and desserts, and vegetarian markers
- **Happy hour section** and a scrolling ticker banner
- **Photo gallery** with a click-to-enlarge lightbox
- **Booking form** that opens the visitor's email app with the details pre-filled (see [Booking form](#booking-form))
- **Opening hours table** that highlights today and fills in the footer's "Open today until" time
- **Social links** for Instagram, Facebook and TikTok
- **Responsive layout** for phones, tablets and desktops
- **Accessibility:** keyboard-friendly tabs and lightbox, descriptive alt text, visible focus styles, and animations switched off for visitors who prefer reduced motion
- **SEO and sharing tags:** page description plus Open Graph and Twitter tags

## Project structure

```
.
├── index.html   # The whole website: HTML, CSS, JavaScript and embedded images
└── README.md
```

Inside `index.html`, the order is:

1. `<head>`: metadata, fonts and all CSS
2. `<nav>`, `<header class="hero">`: navigation and hero
3. `<main>`: story, menu, happy hour, gallery, booking and visit sections
4. `<footer>` and the gallery `<dialog>`
5. A single `<script>` block with the menu tabs, lightbox, opening-hours highlight and booking form

## Running locally

Open `index.html` in any modern browser. No server is required.

## Deployment

Because the site is one static file, it works on any static host:

| Host | Steps |
| --- | --- |
| **Netlify** | Drag the file (or its folder) onto [app.netlify.com/drop](https://app.netlify.com/drop) |
| **GitHub Pages** | Commit `index.html` to a repository, then enable Pages in the repository settings |
| **Traditional web hosting** | Upload `index.html` to the `public_html` (or equivalent) folder over FTP |

## Customisation

### Colours

All colours are CSS variables at the top of the `<style>` block:

```css
:root{
  --bg:#120e0b;      /* page background */
  --amber:#f4b860;   /* accent: headings, prices, buttons */
  --wood:#a8693a;    /* photo borders */
  --leaf:#5cc99a;    /* vegetarian marker */
  ...
}
```

### Fonts

The site uses [Josefin Sans](https://fonts.google.com/specimen/Josefin+Sans) for headings and [DM Sans](https://fonts.google.com/specimen/DM+Sans) for body text, loaded from Google Fonts. If the fonts fail to load, the page falls back to system fonts.

### Menu

Each menu tab is a `<div class="panel">` containing a list. To add or change a dish, edit its list item:

```html
<li><span class="n">Dish name<small>Short description</small></span><i></i><b>R99</b></li>
```

Add the class `veg` to the `<span class="n">` for vegetarian dishes: `<span class="n veg">`.

### Opening hours

Edit the rows in the `<tbody id="hours">` table. Keep the `data-d` attribute (0 = Sunday, 1 = Monday ... 6 = Saturday) and the `8:00 – 21:00` format with an en dash, because the script reads the closing time from it.

### Contact details and social links

Search `index.html` for these and replace them:

- `reservations@obzcafe.co.za` (booking form and contact address)
- `instagram.com/obz_cafe`, `facebook.com/obzcafe`, `tiktok.com/@obz_cafe`
- `115 Lower Main Road` (address and the Google Maps link)

### Images

The photos are embedded directly in the file as base64 `data:` URIs, so the site works as a single file. This makes the file about 1.3 MB.

To use separate image files instead:

1. Create an `images/` folder next to `index.html` and add your photos.
2. Replace each `src="data:image/webp;base64,..."` with `src="images/your-file.webp"`.
3. Some photos appear more than once (for example the dining room, bar and street front), so update every occurrence.

Use WebP or JPEG, around 1000 to 1400 px wide, for a good balance of quality and speed.

## Booking form

The form uses a `mailto:` link. When a visitor submits it, their email app opens with the booking details filled in, and they must press Send. It does not send email by itself, and it will not work for visitors without an email app configured.

For reliable bookings, connect the form to a form service such as [Formspree](https://formspree.io) or [Web3Forms](https://web3forms.com). These receive the form submission and email it to you. This needs the site to be hosted on your own domain or host, and a small change to the form's `action` attribute and submit script.

## Things to verify before going live

Some content was read from low-resolution images or filled in as placeholders:

- **Menu prices and descriptions:** read from a small menu photo, so check each one. Peri Peri Chicken and Steak are left out because their prices were unreadable.
- **Opening hours:** placeholders, not the real hours.
- **Social media handles:** placeholders.
- **Phone number:** not included.
- **Happy hour times:** 5–7 pm, Tuesday to Friday, read from the chalkboard in the photos.
- **Price per person (R200–300) and busiest hours (6–10 pm):** taken from a promotional image.

## Browser support

Current versions of Chrome, Edge, Firefox and Safari. The page uses CSS grid, CSS variables, `<dialog>` and `100svh`, which all older browsers may not support.

## Credits

- Photographs: supplied by OBZ Cafe. Make sure you have the right to publish all of them.
- Fonts: Josefin Sans and DM Sans via Google Fonts (SIL Open Font License).
