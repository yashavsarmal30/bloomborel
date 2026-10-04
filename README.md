# Bloom Borel

[![License: OFL-1.1](https://img.shields.io/badge/License-OFL--1.1-blue.svg)](OFL.txt)
[![Styles: Regular & Italic](https://img.shields.io/badge/Styles-Regular%20%26%20Italic-emerald.svg)](fonts/ttf/)
[![Format: TTF & WOFF2](https://img.shields.io/badge/Format-TTF%20%26%20WOFF2-orange.svg)](fonts/)

**Bloom Borel** is a free, open-source contemporary cursive script typeface family featuring both **Regular** (upright) and **Italic** (12° slant) styles.

Derived from the open-source **Borel** font designed by Rosalie Wagner at the Atelier National de Recherche Typographique (ANRT), Bloom Borel blends the organic fluidity of French school cursive penmanship with the clean, balanced rhythm and restraint of modern digital interface and brand design.

---

## Font Styles & Downloads

Pre-built font files are ready to use in the [`fonts/`](./fonts/) directory:

| Style | PostScript Name | Desktop Format | Web Format |
| :--- | :--- | :--- | :--- |
| **Bloom Borel Regular** | `BloomBorel-Regular` | [`fonts/ttf/BloomBorel-Regular.ttf`](./fonts/ttf/BloomBorel-Regular.ttf) | [`fonts/webfonts/BloomBorel-Regular.woff2`](./fonts/webfonts/BloomBorel-Regular.woff2) |
| **Bloom Borel Italic** | `BloomBorel-Italic` | [`fonts/ttf/BloomBorel-Italic.ttf`](./fonts/ttf/BloomBorel-Italic.ttf) | [`fonts/webfonts/BloomBorel-Italic.woff2`](./fonts/webfonts/BloomBorel-Italic.woff2) |

---

## Key Features

- **Continuous Cursive Flow**: Letters connect seamlessly at the connection baseline using OpenType **Contextual Alternates** (`calt`), recreating the fluidity of authentic handwritten script.
- **Calibrated 12° Italic**: Designed with natural writing momentum and clean proportions, giving words an expressive yet disciplined rhythm.
- **Balanced Monoline Construction**: Smooth, rounded stroke terminals and consistent stroke weight that remain clear and legible across both display and UI text sizes.
- **Over 1,500 Glyphs**: Extensive Latin character coverage including accented characters, numerals, typographic punctuation, and symbols.
- **Production-Ready & Cross-Platform**: Fully compatible with Windows, macOS, Linux, Figma, Adobe Creative Cloud, Microsoft Office, and modern web browsers.

---

## Desktop Installation

### Windows
1. Download or locate [`BloomBorel-Regular.ttf`](./fonts/ttf/BloomBorel-Regular.ttf) and [`BloomBorel-Italic.ttf`](./fonts/ttf/BloomBorel-Italic.ttf) in `fonts/ttf/`.
2. Right-click the font files and select **Install** (or **Install for all users**).
3. The font will immediately appear in your applications under the family name **Bloom Borel**.

### macOS
1. Double-click each `.ttf` file.
2. In the Font Book preview window, click **Install Font**.
3. Verify that **Bloom Borel** is listed with both **Regular** and **Italic** styles.

### Linux
1. Copy the `.ttf` files to your user fonts folder:
   ```bash
   mkdir -p ~/.local/share/fonts
   cp fonts/ttf/*.ttf ~/.local/share/fonts/
   fc-cache -f -v
   ```

---

## Using in Figma

1. After installing the font on your computer, restart Figma completely (or reload the Figma Desktop app).
2. Create a text layer.
3. In the font family dropdown, search for **Bloom Borel**.
4. Choose **Regular** or **Italic**.
5. **Contextual Alternates**: Ensure OpenType contextual alternates are enabled (enabled by default in Figma) to let letter strokes connect naturally.

---

## Web Usage (CSS)

Use the optimized WOFF2 webfonts located in [`fonts/webfonts/`](./fonts/webfonts/):

```css
@font-face {
  font-family: 'Bloom Borel';
  src: url('fonts/webfonts/BloomBorel-Regular.woff2') format('woff2');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'Bloom Borel';
  src: url('fonts/webfonts/BloomBorel-Italic.woff2') format('woff2');
  font-weight: 400;
  font-style: italic;
  font-display: swap;
}

/* Apply to your cursive elements */
.brand-script {
  font-family: 'Bloom Borel', cursive, sans-serif;
  font-weight: 400;
  /* Activate OpenType cursive letter connections */
  font-feature-settings: "calt" 1, "liga" 1, "kern" 1;
  text-rendering: optimizeLegibility;
}
```

---

## OpenType Features

Bloom Borel includes advanced OpenType layout tables:

| Tag | Feature | Function |
| :--- | :--- | :--- |
| `calt` | Contextual Alternates | Dynamically joins cursive exit and entry strokes |
| `liga` | Standard Ligatures | Refined letter-pair connections |
| `kern` | Kerning | Proportional spacing between letter pairs |
| `isol` | Isolated Forms | Natural forms for standalone letters |
| `case` | Case-Sensitive Forms | Adjusts punctuation for uppercase text |
| `ccmp` | Glyph Composition | Proper accent and diacritic positioning |

---

## Character Set & Language Support

Bloom Borel provides extensive character support:
- **Uppercase & Lowercase Latin**: `A-Z`, `a-z`
- **Numerals**: `0-9`
- **Punctuation & Symbols**: `! ? . , : ; ' " ( ) [ ] { } & @ # $ % * / - + = —`
- **Diacritics & Accents**: Full Western and Central European coverage (`À`, `É`, `Ç`, `ñ`, `ü`, `ø`, `œ`, etc.)

---

## License

Bloom Borel is licensed under the **SIL Open Font License, Version 1.1** ([OFL.txt](./OFL.txt)).

You are free to:
- **Use**: Use the font for personal, educational, commercial, printed, or digital projects.
- **Modify**: Study, adapt, and build derivative works.
- **Distribute**: Bundle and distribute the font with any software or design package (free of charge, not sold by itself).

---

## Authors & Credits

- **Original Borel Design**: Rosalie Wagner, ANRT (Atelier National de Recherche Typographique) — [Original Borel Repository](https://github.com/RosaWagner/Borel).
- **Bloom Borel Modifications & Italic Development**: Yash Avsarmal & Bloom Borel Contributors.
- See [`AUTHORS.txt`](./AUTHORS.txt) and [`CONTRIBUTORS.txt`](./CONTRIBUTORS.txt) for copyright and contributor details.
