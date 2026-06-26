# haraldur.pro

Personal website for Haraldur Karlsson. Single-file, no build step.

## Deployment

Deploys automatically to Cloudflare Pages on every push to `main`.

**Before the first deploy**, add this secret to the GitHub repository
(Settings → Secrets and variables → Actions → New repository secret):

| Secret name | Value |
|---|---|
| `CLOUDFLARE_API_TOKEN` | A Cloudflare API token with **Cloudflare Pages: Edit** permission |

## Images

Add these two files to the repository root before deploying:

- `hero.jpg` — full-width banner image (landscape, 1600px+ wide recommended)
- `portrait.jpg` — headshot (square crop, 160px+ recommended)
