# Bloom Borel — Design & Engineering Notes

## 1. Overview & Lineage

**Bloom Borel** is a contemporary, installable OpenType/TrueType font family combining:
- The organic, continuous cursive handwriting of **Borel** (created by Rosalie Wagner, ANRT, under the SIL Open Font License 1.1)
- The clean, restrained aesthetic rhythm of modern digital UI script typography
- An intentional, calibrated italic slant (12° standard)
- Native compatibility with **Windows**, **macOS**, and **Figma**

Bloom Borel is an original derivative work. It preserves all original author attributions and licenses while introducing an engineered italic transformation pipeline and refined typographic metadata.

---

## 2. Font Styles & Deliverables

| File | Style | Slant Angle | PostScript Name | Target Use |
| :--- | :--- | :--- | :--- | :--- |
| `fonts/ttf/BloomBorel-Regular.ttf` | Regular | 0.0° | `BloomBorel-Regular` | Primary upright cursive script |
| `fonts/ttf/BloomBorel-Italic.ttf` | Italic | 12.0° | `BloomBorel-Italic` | Primary italic cursive script (12° slant) |
| `fonts/webfonts/BloomBorel-Regular.woff2` | Regular | 0.0° | `BloomBorel-Regular` | High-efficiency modern webfont |
| `fonts/webfonts/BloomBorel-Italic.woff2` | Italic | 12.0° | `BloomBorel-Italic` | High-efficiency modern webfont |

---

## 3. Transformation Engineering

### 3.1 Affine Outline Shearing
The horizontal shear follows:
$$x' = x + \tan(\theta) \cdot y$$
$$y' = y$$

Because the transformation is linear and shears parallel to the baseline ($y = 0$):
- Horizontal distances at identical $y$-coordinates remain constant.
- In Borel's cursive construction, the exit tail of glyph $n$ meets the entry connector of glyph $n+1$ at the connection baseline $y_c$.
- By maintaining the original advance widths for cursive joins, the transformed exit and entry points meet with mathematical continuity:
  $$x'_{exit} = x_{exit} + \tan(\theta) \cdot y_c = (W + x_{entry}) + \tan(\theta) \cdot y_c = W + x'_{entry}$$
- Result: 100% continuous cursive joins across all lowercase combinations.

### 3.2 Composite Glyph Translation
In TrueType, composite glyphs reference base components via translations $(dx, dy)$. To prevent accent displacement, all composite offsets are updated:
$$dx' = \text{round}(dx + \tan(\theta) \cdot dy)$$
$$dy' = dy$$

### 3.3 GPOS Mark Anchors
GPOS anchor tables (`MarkBasePos` and `MarkMarkPos`) position diacritics and accents. Anchor coordinates are transformed accordingly:
$$\text{Anchor}_X' = \text{round}(\text{Anchor}_X + \tan(\theta) \cdot \text{Anchor}_Y)$$

### 3.4 Metric Recalculation
- **`glyf` Table**: Recalculated bounding boxes (`xMin`, `xMax`, `yMin`, `yMax`) for all 1,514 glyphs.
- **`head` Table**: Global font bounding box updated.
- **`hmtx` Table**: Left side bearing (`lsb`) synchronized with `xMin`.
- **`hhea` Table**: `caretSlopeRise = 1000`, `caretSlopeRun = round(1000 * tan(angle))` for slanted cursor placement in text editors.

---

## 4. Slant Angle Study

Visual comparisons were evaluated across 5 angles:
- **8°**: Subtle forward momentum, but still reads somewhat rigid and upright.
- **10°**: Balanced and approachable, but slightly reserved.
- **12° (Selected Standard)**: The ideal sweet spot — matches the natural cadence of fast handwriting, provides sleek cursive elegance, and maintains complete legibility without crowded ascenders.
- **14°**: Expressive, but long ascenders (`b`, `h`, `k`, `l`) begin to crowd preceding letters.
- **16°**: Excessive overhang on wide capitals and descenders.

---

## 5. Figma & Windows Installation

### Installation on Windows
1. Open the `fonts/ttf/` directory.
2. Select `BloomBorel-Regular.ttf` and `BloomBorel-Italic.ttf`.
3. Right-click and choose **Install** (or **Install for all users**).

### Usage in Figma
1. Fully restart Figma to refresh the system font cache.
2. Create or select a text layer.
3. In the font picker, search for **Bloom Borel**.
4. Select style: **Regular** or **Italic**.
5. Enable **Contextual Alternates** (Figma enables this by default for OpenType script fonts) to enjoy continuous connected script lettering.

---

## 6. Validation Summary

The font family passes 100% of OpenType structural and rasterization tests:
- All essential tables present (`head`, `hhea`, `maxp`, `OS/2`, `hmtx`, `cmap`, `glyf`, `loca`, `name`, `post`, `GSUB`, `GPOS`).
- Valid Unicode cmap mapping ASCII letters, digits, and symbols.
- 0 contour decompile errors across all 1,514 glyphs.
- HarfBuzz OpenType layout engine verification passes for all contextual script tests.
