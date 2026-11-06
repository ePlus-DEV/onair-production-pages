# ePlus OnAir — Production Pages

**Listen Beyond Borders.** This public repository holds the **generated static website** for ePlus OnAir production. It is **not** the source-code repository.

| Property | Value |
| --- | --- |
| Website hostname | https://radio.eplus.dev |
| Source repository | [ePlus-DEV/radio.eplus.dev](https://github.com/ePlus-DEV/radio.eplus.dev) |
| Source branch | `main` |
| GitHub Environment | `production` |
| Published website branch | `main` (this repository) |

> [!IMPORTANT]
> **Generated output — do not manually edit HTML, CSS, JavaScript, radio catalogs, `CNAME` or artwork here.** The next trusted source deployment replaces generated files.

## How releases reach this repository

1. Maintainers review and promote verified `staging` changes into the source `main` branch.
2. [Deploy ePlus OnAir to GitHub Pages](https://github.com/ePlus-DEV/radio.eplus.dev/actions/workflows/deploy-github-pages.yml) builds and tests the website, checks the exact target repository, configured hostname and token permissions, and audits output size.
3. The workflow publishes Nuxt static output to this repository's `main` branch. The root `CNAME` is restored and this `README.md` is preserved by the publishing workflow.
4. This repository's GitHub Pages settings serve branch `main` at `/(root)` for the configured custom domain.

Trusted source `main` pushes trigger the production publishing job after its preflight checks. Feature PRs target `staging`, while reviewed release PRs promote `staging` to `main`.

## Indexing and image policy

**Production is indexable.** The `main` Pages artifact uses `noIndex:false`, canonical URLs, structured data and `https://radio.eplus.dev/sitemap.xml`, and enables GA4 `G-ETDY41KBBJ` on the canonical production hostname. Staging (`staging` → `stg.radio.eplus.dev`) remains `noindex` with no production GA4 or sitemap. DNS/TLS and cache routing must still be verified separately from a successful Pages push.

Regular website builds use `npm run generate:site`, retaining station logos but excluding the large per-station Open Graph JPEG collection so the published site stays under the GitHub Pages **1 GB site limit**.

Per-station Open Graph JPEG uploads are not part of the current publishing workflow. Use the shared brand social image unless a separately verified external image manifest is configured.

## Maintainership

- Make application, station-data, player, SEO, or CI changes **in the source repository** through pull requests.
- Check source [README](https://github.com/ePlus-DEV/radio.eplus.dev/blob/main/README.md) and [deployment guide](https://github.com/ePlus-DEV/radio.eplus.dev/blob/main/docs/GITHUB_PAGES.md) for the branch map, configuration and release procedure.
- Never commit deployment tokens, private configuration or credentials into this public repository.
- If this README disappears after a redeploy, verify that the source publisher still excludes `/README.md` when syncing with `rsync --delete`.

Maintained by **ePlus.DEV** · ePlus OnAir — Listen Beyond Borders.
