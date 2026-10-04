# Genuary Word — Generative Art

> A seed-based generative system for pixel-grid letterform compositions.  
> A reproducible catalogue of computational typographic studies.

---

## What is this?

**Genuary Word** is a generative design system that takes the seven letters of the word GENUARY and rebuilds them as pixel grids — each letter a 5 × 7 matrix of ones and zeros. Every "on" cell is rendered as a block: a rectangle, a circle, or a rounded square, chosen once per composition. A gradient background and film grain complete the field.

Every artwork in this catalogue is defined by a single numeric seed. The same seed always produces the identical composition — making each piece **traceable, reproducible, and licensable** across textile, print, and apparel applications.

Named for the annual generative art challenge it was originally made for, **Genuary Word** reframes typography as a textile.

---

## Live

🌐 **[View the catalogue →](https://reyrove.github.io/Genuary-Word-Generative-Art/)**

---

## The System

The generator combines three layers:

| Layer | Description |
|-------|-------------|
| **Gradient ground** | Two palette colours blended across 150 horizontal hairlines. |
| **Pixel letters** | The word GENUARY, decomposed into 7 pixel grids, each cell drawn as a block. |
| **Film grain** | Seeded noise dots scattered over the whole canvas. |

All three layers are driven by the same seed, ensuring deterministic output.

### Parameters

- **Word** — GENUARY (7 letters)
- **Letter grids** — 5 × 7 pixel matrices
- **Palette** — 1 of 4 curated five-colour sets
- **Block type** — rect, circle, or rounded (chosen per seed)
- **Cell jitter** — ±s × 0.05 per block
- **Background bands** — 150 hairlines
- **Grain density** — 2% of canvas area
- **Stroke weight** — `cellSize × 0.18`

---

## Structure

```
Genuary-Word-Generative-Art/
├── index.html              ← Full catalogue (single-file)
├── images/
│   ├── fav.svg
│   ├── genuary-tote.png
│   ├── genuary-cushion.png
│   └── ...
├── Genuary-Word.jpg        ← Apparel mockup
└── README.md
```

The entire project is contained in a single `index.html` — no build step, no framework. The only external dependency is **p5.js** (loaded from CDN), which drives the exact sketch pipeline.

---

## Features

- **Seed-based generation** — every composition is deterministic and reproducible
- **Same seed, many surfaces** — the plate, cover, framed print, and all four surface swatches render from the same seed
- **Tiled rectangular surfaces** — scarves, textiles, and wallpaper tile the square composition to fill their aspect ratio, preserving the visual identity
- **Archive of 8 seeds** — each thumbnail is a *different* composition; click one to load it into the plate, and every surface follows
- **Live animation** — the plate runs continuously; the cover and framed plate auto-stop after 2 seconds
- **PNG export** — download the current frame of the plate directly from the browser
- **Keyboard shortcuts** — `R` for new seed, `S` to save
- **Legal modal** — licensing, terms, and credits built in
- **Responsive** — works on desktop, tablet, and mobile
- **Mobile-first navbar** — horizontally scrollable with fade hint

---

## Usage

### Generate a new composition

Click **New Seed** or press `R`.

### Download the current frame

Click **Download** or press `S`.

### Load a seed from the archive

Click any plate in the **Archive** section. The plate, cover, framed print, and every surface swatch update to that seed.

---

## Color System

Every composition is drawn from one of four curated five-colour palettes:

| Palette | Character |
|---------|-----------|
| **Navy · Slate · Teal · Lime · Amber** | Deep, cool, with a warm accent |
| **Black · Magenta · Violet · Sky · Yellow** | High-contrast neon set |
| **Night · Steel · Teal · White · Orange** | Cool, graphic, with a bright sun |
| **Ocean · Graphite · Slate · Bone · Coral** | Muted, editorial, with a pink accent |

Each seed picks one palette, one stroke colour from that palette, and one block type. The blocks themselves are individually sampled from the palette, so every cell carries a different tint even within a single letter.

Because the seed picks both the palette and the block type, no two compositions share the same rhythm of colour and shape.

---

## Surfaces — one seed, many ratios

Every surface in the catalogue is drawn from the same seed. The rectangular surfaces tile the square composition to fill their aspect ratio:

| Surface | Ratio | Tiling |
|---------|-------|--------|
| **Print** | 1 : 1 | 1 × 1 — identical to the plate |
| **Scarf** | 3 : 1 | 3 × 1 — composition repeated 3× horizontally |
| **Textile** | 4 : 3 | 2 × 2 — composition repeated 2× in both directions |
| **Wall** | 2 : 3 | 1 × 2 — composition repeated 2× vertically |

Every tile uses the same seed with a fresh RNG reset, so all tiles are visually identical. This is exactly what a repeat pattern looks like — one motif, tiled.

---

## Technical Notes

- **p5.js** drives the composition. `rect()`, `ellipse()`, `stroke()`, and `fill()` are used natively.
- **Seeded randomness** uses a Lehmer LCG. Same seed → same palette, same block type, same letter rendering, same grain.
- **Live plate** — 30fps. The plate's `draw()` runs continuously until the page is hidden.
- **Cover and framed plate** — 20fps, auto-stop after 2 seconds.
- **Frozen stills** — the four surface swatches and eight archive thumbnails run 2 frames then freeze.
- **Fast grain** — the original `loadPixels()` / `updatePixels()` approach is very slow for a catalogue (millions of pixels per frame). This uses a seeded dot-based grain at 2% canvas density instead — visually identical, dramatically faster.
- **Off-screen pause** — an `IntersectionObserver` calls `noLoop()` on live instances that scroll out of view.
- **`prefers-reduced-motion` respected.**

---

## About

**Genuary Word** is a project by [Reyhaneh Daneshdoost](https://reyrove.github.io/) — an Iranian-born artist working at the intersection of classical textile logic and generative systems.

The work begins with a simple observation: the woven surface — repetitive, mathematically structured, infinitely variable — has always been a form of computation, long before computers.

**Genuary Word** is an attempt to render that logic visible.

> *A letter drawn in a grid stops being a word and becomes a field of blocks.*

---

## Licensing

All compositions are seed-documented and available for licensing across textile, surface, and apparel applications.

For commercial use, custom editions, or exclusive rights:

📧 **reyhanehdaneshdoost@gmail.com**

See the **Licensing** section in the live catalogue for details.

---

## Links

- 🌐 [Website](https://reyrove.github.io/)
- 📷 [Instagram](https://www.instagram.com/rey._.rove/)
- 💼 [LinkedIn](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- 🐦 [X](https://x.com/reyrove)

---

## Credits

**Design & Generative System**  
Reyhaneh Daneshdoost

**Typefaces**  
Cormorant Garamond · DM Mono

**Edition**  
Genuary Word — Autumn 2026

---

<p align="center">
  <em>Generative Pixel Letters</em><br />
  <sub>© Reyrove Studio · All compositions reproducible by seed</sub>
</p>