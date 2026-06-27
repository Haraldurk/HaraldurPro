# HaraldurPro — Claude Code Notes

Single-file site: `index.html`. All CSS is inline in `<style>`. All JS is inline at the bottom. No build step.

## Sections (in DOM order)
- NAV → HERO → INTRO → SERVICES → PARTNERS → ABOUT → CONTACT → FOOTER

## Partners section (`/images/partners/`)
The "Selected work with" strip sits between SERVICES and ABOUT. 21 institutions total.

### Label convention
Show `<span class="partner-name">` under **all** partner logos — every item has a name label.

### All logos (21 institutions)

| File | Institution | Type | Label? |
|------|-------------|------|--------|
| `listasafn-islands.svg` | Listasafn Íslands | LÍ monogram (created) | ✓ |
| `listasafn-reykjavikur-logo.png` | Listasafn Reykjavíkur | 3D triangle mark (from user-provided JPG, white on transparent) | ✓ |
| `listasafn-akureyrar-real.png` | Listasafn Akureyrar | PNG logo (downloaded from lam.is, RGBA transparent, uses `.logo-invert` CSS filter) | — |
| `nylistasafnid-logo.png` | Nýlistasafnið | diagonal mark (from user-provided JPG, white on transparent) | — |
| `kunstnerneshus-real.svg` | Kunstnernes Hus | lion mark (downloaded safari-pinned-tab, fill converted to white) | ✓ |
| `ateliernord_compass.svg` | Atelier Nord | abstract mark (downloaded, already white) | ✓ |
| `vasulkakitchen-logo.png` | Vasulka Kitchen Brno | branding image (from user-provided JPG, white marks on transparent) | — |
| `nime.svg` | NIME Conference | boxed letterform (downloaded, colors fixed to white) | ✓ |
| `insomnia.svg` | Insomnia Festival | wordmark (created) | — |
| `dansenshus-real.svg` | Dansens Hus | inline SVG from dansenshus.com (text wordmark, fill set to white) | — |
| `okno.svg` | Okno | wordmark (created) | — |
| `steim-real.png` | STEIM | RGBA PNG (downloaded from steim.org CSS background-image, uses `.logo-invert`) | — |
| `atopia.svg` | Atopia | wordmark (created) | — |
| `raflost-real.png` | RAFLOST | PNG logo (downloaded from raflost.is, RGBA transparent, uses `.logo-invert` CSS filter) | — |
| `reykjavik.svg` | Reykjavíkurborg | city mark (downloaded from styles.reykjavik.is, colors converted to white) | ✓ |
| `veitur-real.svg` | Veitur | inline SVG from veitur.is (wordmark, CSS class fills converted to white) | — |
| `taekniminjasafn-real.png` | Tækniminjasafn Austurlands | indexed PNG with tRNS (downloaded from tekmus.is, uses `.logo-invert`) | — |
| `lhi.svg` | Listaháskóli Íslands (LHÍ) | text mark (downloaded, already white) | — |
| `sim-logo.png` | SÍM | mark (from user-provided AVIF, white on transparent) | — |
| `pori.svg` | Pori Art Museum / Porin taidemuseo | text mark (downloaded, colors converted to white) | — |
| `lapinamk-logo.png` | Lapin AMK | wordmark (from user-provided PNG, black on white inverted to white on transparent) | — |

### SVG color convention
All logos must be **white fills on transparent background**. When converting downloaded SVGs:
- Replace all named color fills with `#ffffff`
- Remove white/background-colored shield/frame fills (`fill="none"`)
- Use `replace_all` in Edit tool for consistent substitution
- CSS normalization: `.partner-logo { opacity: 0.4; }` at rest, `opacity: 0.7` on hover
- For RGBA PNGs with dark marks on transparent: add class `logo-invert` (applies `filter: brightness(0) invert(1)`) — works regardless of original mark color
- All `.partner-item` blocks are wrapped in `<a href="..." target="_blank" rel="noopener">` links
- `.partners-strip a` has `text-decoration: none; color: inherit`

### To add a new partner
1. Save SVG (white on transparent) or RGBA PNG to `images/partners/`
2. Wrap a `<a href="..."><div class="partner-item">` block in PARTNERS section in `index.html`
3. Add class `logo-invert` to `<img>` if using a PNG with dark marks on transparent background
4. Add `<span class="partner-name">` only if the mark is abstract/graphic (not a text wordmark)
5. Update this table above

## i18n
Three languages: `en`, `is`, `no`. All strings in the `strings` object in the inline `<script>`. The PARTNERS section label ("Selected work with") is currently hard-coded English — add i18n keys if multilingual support is needed there.

## Deployment
Cloudflare Pages via `wrangler pages deploy`. Project name: `haraldur-pro`.
