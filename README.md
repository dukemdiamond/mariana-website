# Mariana Roa — portfolio

A one-page site for Mariana Roa: Biology and Political Science at Northeastern,
Patient Care Technician in Beth Israel's Cardiac ICU, future pediatric nurse.

Static HTML and CSS, plus a few lines of inline script for the banner's
scrolled state. No build step — open `index.html`, or serve the folder:

```sh
python3 -m http.server 8000
```

## Structure

```
index.html    # intro, experience, footer
styles.css    # design tokens + all component styles
assets/       # portrait, Monet background, favicon
```

The page is: a full-bleed intro over the painting, an experience list, and a
footer. Email, phone and LinkedIn are inline icon links in both the intro and
the footer — no modal, nothing to click through.

The banner is sticky and transparent while it sits over the painting; a scroll
listener adds `.nav--stuck` past 24px to fade in a translucent fill, so it
never draws a hard edge against the artwork. `--nav-h` in `:root` must match
the banner's real height — `.hero__bg` uses it to bleed the painting up behind
the transparent bar.

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

`assets/mariana-portrait.jpg` is a square crop of `IMG_3869.HEIC`:

```sh
sips -s format jpeg -s formatOptions best IMG_3869.HEIC --out full.jpg
ffmpeg -i full.jpg -vf "crop=1600:1600:1340:620,scale=760:760" -q:v 3 assets/mariana-portrait.jpg
```

The x offset of 1340 is deliberate: anything further left catches the door
frame at the edge of the original frame.

## Copy

The intro paragraph is Mariana's own wording. Experience bullets come from her
résumé, lightly edited to present tense. Nothing on the page is invented.
