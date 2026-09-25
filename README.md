# Mariana Roa — portfolio

A one-page site for Mariana Roa: Biology and Political Science at Northeastern,
Patient Care Technician in Beth Israel's Cardiac ICU, future pediatric nurse.

Static HTML and CSS, one small inline script for the contact dialog. No build
step — open `index.html`, or serve the folder:

```sh
python3 -m http.server 8000
```

## Structure

```
index.html    # intro, experience, contact dialog
styles.css    # design tokens + all component styles
assets/       # portrait, Monet background, favicon
```

The page is: a full-bleed intro over the painting, an experience list, and a
footer. "Get in touch" (hero and footer) opens a native `<dialog>` with email,
phone, and LinkedIn.

## Design

Adapted from `DESIGN-stripe.md` — Inter at weight 300 with negative
letter-spacing, `ss01` globally, `tnum` on numeric cells, pill buttons at
`8px 16px`, 12px card radii, hairline borders — with indigo swapped for sage
green (`#4a6d47` → `#3a4a37` → `#2a332a`, ink `#2a332a`, canvas `#fdfefb`).
Those greens are sampled from [adaline.ai](https://www.adaline.ai).

The hero backdrop is Monet's *Antibes, Afternoon Effect* (MFA Boston). Two
scrims sit over it: a left-weighted warm-white gradient, plus a radial halo
behind the copy so the text clears the painting's busy mid-ground. On one
column the left gradient becomes a top-down one. Both are tuned to keep the
painting visible — if you darken them further the Monet stops reading.

Tokens live in `:root` at the top of `styles.css`.

## Photography

`assets/mariana-portrait.jpg` is a 2:3 crop of `IMG_3869.HEIC`:

```sh
sips -s format jpeg -s formatOptions best IMG_3869.HEIC --out full.jpg
ffmpeg -i full.jpg -vf "crop=1555:2304:1354:662,scale=1100:-2" -q:v 4 assets/mariana-portrait.jpg
```

## Copy

The intro paragraph is Mariana's own wording. Experience bullets come from her
résumé, lightly edited to present tense. Nothing on the page is invented.
