# Mariana Roa — portfolio

A single-page portfolio for Mariana Roa: Patient Care Technician in the Cardiac
ICU at Beth Israel Deaconess Medical Center, Biology and Political Science
student at Northeastern, and aspiring nurse.

Static HTML and CSS. No build step — open `index.html`, or serve the folder:

```sh
python3 -m http.server 8000
```

## Structure

```
index.html    # the whole page
styles.css    # design tokens + all component styles
assets/       # portrait, headshot, favicon
```

## Design

The design system is adapted from `DESIGN-stripe.md`, with two substitutions:

- **Indigo → sage green.** The CTA/accent ramp is `#4a6d47` → `#3a4a37` →
  `#2a332a`, with `#d8e3dd` as the subdued fill. Green tones are sampled from
  [adaline.ai](https://www.adaline.ai): forest ink `#2a332a`, pale sage
  `#e1e6df` / `#d8e3dd`, warm white `#fdfefb`.
- **Gradient mesh → sage wash.** The hero backdrop is an inline SVG of blurred
  ellipses in sage, mint and warm cream, faded into the canvas at its lower
  edge. Kept as SVG rather than CSS gradients so the blobs stay organic.

Everything else follows the source system: Inter at weight 300 with negative
letter-spacing on display tiers, `ss01` globally, `tnum` on any numeric cell,
pill buttons at `8px 16px`, 12px card radii, hairline borders, and the two
shadow levels.

Tokens live in `:root` at the top of `styles.css`.

## Photography

`assets/mariana-portrait.jpg` (2:3) and `assets/mariana-headshot.jpg` (1:1) are
crops of a single source photo, generated with:

```sh
sips -s format jpeg -s formatOptions best IMG_3869.HEIC --out full.jpg
ffmpeg -i full.jpg -vf "crop=1555:2304:1354:662,scale=1100:-2" -q:v 4 assets/mariana-portrait.jpg
ffmpeg -i full.jpg -vf "crop=1250:1250:1405:750,scale=700:700"  -q:v 4 assets/mariana-headshot.jpg
```

## Copy

Résumé content — roles, bullets, dates, coursework, certifications, contact
details — is taken verbatim or lightly edited from Mariana's résumé.

The connective first-person narrative (hero lead, the About section, the
"Working with kids" intro, and the pull quote) is **drafted, not dictated**. It
should be read and approved by Mariana before the site is shared, since it
speaks in her voice.
