# HaraldurPro — Claude Code Notes

Single-file site: `index.html`. All CSS is inline in `<style>`. All JS is inline at the bottom. No build step.

## Sections (in DOM order)
- NAV → HERO → INTRO → SERVICES → PARTNERS → ABOUT → CONTACT → FOOTER

## Partners section (`/images/partners/`)
The "Selected work with" strip sits between SERVICES and ABOUT. 14 institutions.

**Convention for logos:**
- All files live in `images/partners/`
- Preferred format: SVG with white fills on transparent background
- SVG wordmarks (text-based): created locally for institutions where a downloadable SVG was unavailable
- Downloaded SVG marks: `nime.svg` (NIME Conference, white text/border), `ateliernord_compass.svg` (Atelier Nord abstract mark, already white)
- CSS normalization: `.partner-logo { opacity: 0.4; }` on all logos — no filter needed since all files use white fills
- Hover: `opacity: 0.7`

**To add a new partner:** add the SVG to `images/partners/`, add a `.partner-item` block in the PARTNERS section of `index.html`.

## i18n
Three languages: `en`, `is`, `no`. All strings in the `strings` object in the inline `<script>`. The PARTNERS section label ("Selected work with") is currently hard-coded English — add i18n keys if multilingual support is needed there.

## Deployment
Cloudflare Pages via `wrangler pages deploy`. Project name: `haraldur-pro`.
