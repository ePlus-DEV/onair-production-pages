# ePlus OnAir — Production Pages

**Listen Beyond Borders.** This public repository holds the **generated static website** for ePlus OnAir production. It is **not** the source-code repository.

| Property | Value |
| --- | --- |
| Website hostname | https://radio.eplus.dev |
| Private source repository | [ePlus-DEV/radio.eplus.dev](https://github.com/ePlus-DEV/radio.eplus.dev) |
| Source branch | `main` |
| GitHub Environment | `production` |
| Published website branch | `main` (this repository) |
| Optional social-image branch | `station-images` (not the Pages website branch) |

> [!IMPORTANT]
> **Generated output — do not manually edit HTML, CSS, JavaScript, radio catalogs, `CNAME` or artwork here.** The next trusted source deployment replaces generated files.

## How releases reach this repository

1. Maintainers review and merge changes into the private source `main` branch.
2. [Deploy ePlus OnAir to GitHub Pages](https://github.com/ePlus-DEV/radio.eplus.dev/actions/workflows/deploy-github-pages.yml) builds and tests the website, checks the exact target repository, configured hostname and token permissions, and audits output size.
3. The workflow publishes Nuxt static output to this repository's `main` branch. The root `CNAME` is restored and this `README.md` is preserved by the publishing workflow.
4. This repository's GitHub Pages settings serve branch `main` at `/(root)` for the configured custom domain.

Trusted source `main` pushes trigger the production publishing job after its preflight checks.

## Indexing and image policy

**Production is indexable.** The `main` Pages artifact uses `noIndex:false`, canonical URLs, structured data and `https://radio.eplus.dev/sitemap.xml`, and enables GA4 `G-ETDY41KBBJ` on the canonical production hostname. Staging (`develop`) remains `noindex` with no production GA4 or sitemap. DNS/TLS and cache routing must still be verified separately from a successful Pages push.

Regular website builds use `npm run generate:site`, retaining station logos but excluding the large per-station Open Graph JPEG collection so the published site stays under the GitHub Pages **1 GB site limit**.

The optional [Publish station images separately](https://github.com/ePlus-DEV/radio.eplus.dev/actions/workflows/publish-station-images.yml) workflow uses an independent `station-images` branch, uploads updated JPEGs in batches of at most 100 MiB, and reports an immutable base URL only once the manifest is complete. Do not copy these JPEGs into website `main`.

## Maintainership

- Make application, station-data, player, SEO, or CI changes **in the private source repository** through pull requests.
- Check source [README](https://github.com/ePlus-DEV/radio.eplus.dev/blob/main/README.md) and [deployment guide](https://github.com/ePlus-DEV/radio.eplus.dev/blob/main/docs/GITHUB_PAGES.md) for the branch map, configuration and release procedure.
- Never commit deployment tokens, private configuration or credentials into this public repository.
- If this README disappears after a redeploy, verify that the source publisher still excludes `/README.md` when syncing with `rsync --delete`.

Maintained by **ePlus.DEV** · ePlus OnAir — Listen Beyond Borders.
