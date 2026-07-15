---
kind: frontend_style
name: Tailwind CSS Single-File Styling with Custom Brand Tokens
category: frontend_style
scope:
    - '**'
source_files:
    - index.html
---

The NutriTrack SPA uses a single-file styling approach built entirely on Tailwind CSS, loaded via CDN (`https://cdn.tailwindcss.com`) and configured inline in the `<head>` of `index.html`. There are no external `.css` or `.scss` files — all visual presentation lives inside one HTML document.

**System & tools**
- **Tailwind CSS (CDN)**: utility-first classes compose every layout, spacing, color, and typography decision. The build step is absent; Tailwind runs client-side from the CDN script tag.
- **Inline config**: a small `tailwindcss.config` object extends the default theme by adding a custom `brand.*` color scale (50–900) centered on emerald green (`#10b981`), which becomes the application's primary semantic palette.
- **Embedded `<style>` block**: only ~20 lines of hand-written CSS exist for things Tailwind cannot express cleanly — CSS custom property `--p` driving an SVG ring chart via `stroke-dashoffset`, keyframe animations (`fadeIn`, `slideIn`), hover/active transitions, and a thin scrollbar style.
- **Google Fonts**: `Noto Sans Thai` is imported at the top of the embedded stylesheet and applied to `body`, ensuring Thai glyphs render correctly across devices.
- **No component library, CSS-in-JS, or preprocessors**: there is no SCSS, PostCSS, CSS Modules, styled-components, or similar tooling.

**Architecture & conventions**
- **Single source of truth**: `index.html` is both markup and style — no separation between structure and presentation. This keeps the app trivially deployable as a static file but means styles are not reusable across components.
- **Design tokens via Tailwind colors**: the sole design token is the `brand` palette. All brand-colored elements reference `brand-50` through `brand-900`; neutral surfaces use Tailwind's gray scale (`gray-50` … `gray-400`). Semantic meaning is conveyed through these tokens rather than custom class names.
- **Responsive strategy**: purely responsive via Tailwind's breakpoint prefixes (`sm:`, `md:`). The layout switches from single-column to two-column grids at `md` and adapts form fields with `grid-cols-1 sm:grid-cols-2`.
- **Animation convention**: motion is kept minimal — CSS transitions on `transform`/`opacity` for hover states, and two named keyframes (`fadeIn`, `slideIn`) for list entry. No animation libraries are used.
- **SVG charts**: the calorie ring is pure SVG with a linear gradient (`#34d399` → `#059669`) defined in `<defs>` and animated by toggling `stroke-dashoffset` via a CSS variable set from JavaScript.

**Rules developers should follow**
1. **Do not create separate CSS/SCSS files** — keep all styling in `index.html` under the existing `<style>` block or as Tailwind utility classes directly on elements.
2. **Use the `brand.*` color scale** for any new UI element that carries brand semantics; fall back to Tailwind's gray palette for neutrals.
3. **Prefer Tailwind utilities over custom CSS**. Only add to the embedded `<style>` block when Tailwind cannot express the rule (e.g., SVG `stroke-dashoffset`, `@keyframes`).
4. **Keep animations subtle and consistent**: reuse the existing `fade-in`, `slide-in`, and transition patterns rather than inventing new ones.
5. **Maintain Thai font support**: any new text must remain legible in Noto Sans Thai; avoid importing additional typefaces unless necessary.