# HaraldurPro — Claude Code Notes

Single-file site: `index.html`. All CSS is inline in `<style>`. All JS is inline at the bottom. No build step.

## Sections (in DOM order)
- NAV → HERO → INTRO → SERVICES → PARTNERS → ABOUT → CONTACT → FOOTER

## Partners section (`/images/partners/`)
The "Selected work with" strip sits between SERVICES and ABOUT. 21 institutions total.

### Label convention
Show `<span class="partner-name">` **only** for graphic/abstract marks where the mark itself does not legibly spell out the institution name:
- **Keep label**: Atelier Nord (abstract compass mark), LÍ / Listasafn Íslands (monogram), NIME (boxed letterform mark), Reykjavíkurborg (logo says "Reykjavík", not the full org name)
- **No label**: all text wordmark SVGs — the name is already in the mark

### All logos (21 institutions)

| File | Institution | Type | Label? |
|------|-------------|------|--------|
| `listasafn-islands.svg` | Listasafn Íslands | LÍ monogram (created) | ✓ |
| `listasafn-reykjavikur.svg` | Listasafn Reykjavíkur | wordmark (created) | — |
| `listasafn-akureyrar.svg` | Listasafn Akureyrar | wordmark (created) | — |
| `nylistasafnid.svg` | Nýlistasafnið | wordmark (created) | — |
| `kunstnerneshus.svg` | Kunstnernes Hus | wordmark (created) | — |
| `ateliernord_compass.svg` | Atelier Nord | abstract mark (downloaded, already white) | ✓ |
| `vasulkakitchen.svg` | Vasulka Kitchen Brno | wordmark (created) | — |
| `nime.svg` | NIME Conference | boxed letterform (downloaded, colors fixed to white) | ✓ |
| `insomnia.svg` | Insomnia Festival | wordmark (created) | — |
| `dansenshus.svg` | Dansens Hus | wordmark (created) | — |
| `okno.svg` | Okno | wordmark (created) | — |
| `steim.svg` | STEIM | wordmark (created) | — |
| `atopia.svg` | Atopia | wordmark (created) | — |
| `raflost.svg` | RAFLOST | wordmark (created) | — |
| `reykjavik.svg` | Reykjavíkurborg | city mark (downloaded from styles.reykjavik.is, colors converted to white) | ✓ |
| `veitur.svg` | Veitur | wordmark (created) | — |
| `taekniminjasafn.svg` | Tækniminjasafn Austurlands | wordmark (created) | — |
| `lhi.svg` | Listaháskóli Íslands (LHÍ) | text mark (downloaded, already white) | — |
| `sim.svg` | SÍM | wordmark (created) | — |
| `pori.svg` | Pori Art Museum / Porin taidemuseo | text mark (downloaded, colors converted to white) | — |
| `lapinamk.svg` | Lapin AMK | wordmark (created) | — |

### SVG color convention
All logos must be **white fills on transparent background**. When converting downloaded SVGs:
- Replace all named color fills with `#ffffff`
- Remove white/background-colored shield/frame fills (`fill="none"`)
- Use `replace_all` in Edit tool for consistent substitution
- CSS normalization: `.partner-logo { opacity: 0.4; }` at rest, `opacity: 0.7` on hover — no CSS filter needed since all files use white fills

### To add a new partner
1. Save SVG to `images/partners/` (white on transparent)
2. Add `.partner-item` block to PARTNERS section in `index.html`
3. Add label only if the mark is abstract/graphic
4. Update this table above

## i18n
Three languages: `en`, `is`, `no`. All strings in the `strings` object in the inline `<script>`. The PARTNERS section label ("Selected work with") is currently hard-coded English — add i18n keys if multilingual support is needed there.

## Deployment
Cloudflare Pages via `wrangler pages deploy`. Project name: `haraldur-pro`.
