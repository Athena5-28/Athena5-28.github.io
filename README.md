# BioMem

A lightweight, accessible single-page company website for BioMem, an early-stage research project in Helsinki, Finland. Plain HTML and CSS, with no JavaScript, build process, external fonts, analytics, or runtime dependencies.

## Files and local preview

- `index.html`: page content, inline conceptual SVG illustration, SEO and Open Graph metadata.
- `styles.css`: responsive layout, focus styles, and reduced-motion support.
- `favicon.svg`: replaceable BioMem favicon.
- `.nojekyll`: serves these static files without Jekyll processing.

Open `index.html` directly, or serve this directory with any static HTTP server. With Python installed:

```sh
python -m http.server 8080 --bind 127.0.0.1
```

Then visit `http://127.0.0.1:8080/`. Nothing needs to be built or installed for production. `.preview/` is ignored local QA output; do not upload it.

## Content to replace

The requested `hello@biomem.example` is a placeholder, not a working contact address. Replace every occurrence in `index.html` (visible text and both `mailto:` links), and remove the adjacent placeholder notice. The `CONTACT` comment locates the contact section. Replace the non-interactive LinkedIn “coming soon” span with a link to the verified company page when available. GitHub already links to `https://github.com/Athena5-28`.

All technology copy describes research and development. The illustration is conceptual and does not represent validated device performance. Update claims only when evidence supports them.

## Publish to GitHub Pages

The owner and hosting account must remain **Athena5-28**, using **Athena5-28/Athena5-28.github.io**.

1. Sign in to the existing Athena5-28 account. Open [the repository](https://github.com/Athena5-28/Athena5-28.github.io). If it does not exist, create a public repository named `Athena5-28.github.io` under that account. GitHub Free requires a public repository for Pages.
2. Commit the website files to `main`, with `index.html` at the repository root. Preserve any existing repository history and unrelated files. Include `.nojekyll`.
3. Open [Settings → Pages](https://github.com/Athena5-28/Athena5-28.github.io/settings/pages).
4. Under **Build and deployment**, choose **Deploy from a branch**, branch **main**, directory **/(root)**, then **Save**.
5. Check the repository's **Actions** tab for a successful Pages deployment. Branch-based publishing still runs deployment through GitHub Actions.
6. Visit [https://athena5-28.github.io/](https://athena5-28.github.io/) and confirm the BioMem page, favicon, and styling appear. Test Technology, Research, About, Contact, and both hero buttons, then check on a phone.

After Pages is enabled, pushing updated files to `main` is sufficient. No custom workflow, build command, environment variables, or hosting service is needed. Do not consider the site deployed until the Actions job succeeds and the live URL serves the expected content.

Official references: [publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site), [creating a Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site).

## Connect a BioMem custom domain later

Keep the same Athena5-28 repository and Pages deployment. All navigation uses page fragments, and assets use relative paths, so no site restructuring is required. No placeholder `CNAME` is included because a domain has not been selected.

1. Register your chosen domain, such as `biomem.ai`, `biomem.bio`, or `biomem.tech`. These are examples, not claims of ownership or availability.
2. Verify domain ownership in the Athena5-28 account's Pages settings using GitHub's supplied TXT record. Follow [GitHub's domain verification guide](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages).
3. In this repository's **Settings → Pages → Custom domain**, enter the chosen bare hostname, such as `biomem.ai` (without `https://` or a path), and save it **before configuring DNS**. With branch publishing, GitHub creates a root `CNAME` file containing that hostname. Pull and retain that file in subsequent changes.
4. At the domain's DNS provider, set the records below. `@` means the apex domain. The `www` target must remain the original GitHub Pages hostname, without a scheme or path.

| Type | Name | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | athena5-28.github.io |
| AAAA (optional) | @ | 2606:50c0:8000::153 |
| AAAA (optional) | @ | 2606:50c0:8001::153 |
| AAAA (optional) | @ | 2606:50c0:8002::153 |
| AAAA (optional) | @ | 2606:50c0:8003::153 |

Use all four A records. An apex ALIAS/ANAME pointing to `athena5-28.github.io` is a supported alternative when offered by the DNS provider. Replace conflicting records for the website hostname, but preserve unrelated mail and verification records. Avoid wildcard DNS records. For a custom subdomain instead of the apex, use a CNAME for that subdomain pointing to `athena5-28.github.io`.

5. Wait for DNS propagation and GitHub's domain check and certificate provisioning. Availability of **Enforce HTTPS** can take up to 24 hours. Select it once available. GitHub can redirect between apex and `www` when both are configured, using the hostname saved in Pages as the preferred domain.
6. In `index.html`, find the `DOMAIN` comment and replace the two initial absolute URLs in `link[rel="canonical"]` and `meta[property="og:url"]` with the final HTTPS URL, including the trailing slash. No hostname occurs in navigation or asset paths. If a social preview image is added later, update its absolute `og:image`/Twitter image URLs too; no social image is currently included.
7. Push the metadata update, wait for Pages deployment, and verify the final domain, HTTPS, redirects, favicon, styling, and section links. Update the public company URL on LinkedIn and application materials.

DNS values checked against official GitHub documentation on 2026-09-17. Recheck the documentation when connecting a domain: [custom domain setup](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site), [HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https), [domain behavior](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages).
