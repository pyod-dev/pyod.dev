# pyod.dev: The PyOD Ecosystem site

Static single-page site for the PyOD open-source anomaly-detection ecosystem.
There is no build step. `index.html` is self-contained: inline CSS and JavaScript,
an inline SVG favicon, and no external requests.

## Files

- `index.html`: the site. Edit the copy and numbers directly.
- `CNAME`: the custom domain for GitHub Pages (`pyod.dev`).

## Deploy on GitHub Pages (org `pyod-dev`)

1. Create the organization at https://github.com/organizations/new and name it `pyod-dev`.
2. Create a public repo under it, for example `pyod-dev/pyod.dev`.
3. Push these files to the default branch (`main`).
4. Repo Settings > Pages > Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
5. Repo Settings > Pages > Custom domain: `pyod.dev` (the `CNAME` file already sets this).
   Turn on "Enforce HTTPS" once GitHub issues the certificate.

## DNS on Namecheap (domain `pyod.dev`)

1. Namecheap > Domain List > Manage `pyod.dev` > Advanced DNS.
2. Keep the nameservers on "Namecheap BasicDNS" (the default). PremiumDNS is not needed.
3. Delete the records Namecheap adds by default: the `CNAME` on host `www` pointing to a
   parking page, and any `URL Redirect` or `A` record on host `@`.
4. Add these host records:

```
Type    Host   Value                    TTL
A       @      185.199.108.153          Automatic
A       @      185.199.109.153          Automatic
A       @      185.199.110.153          Automatic
A       @      185.199.111.153          Automatic
AAAA    @      2606:50c0:8000::153      Automatic
AAAA    @      2606:50c0:8001::153      Automatic
AAAA    @      2606:50c0:8002::153      Automatic
AAAA    @      2606:50c0:8003::153      Automatic
CNAME   www    pyod-dev.github.io.      Automatic
```

`.dev` is HTTPS-only (it sits on the HSTS preload list), so the site will not load over
plain HTTP. GitHub Pages issues a free certificate automatically once DNS resolves and
the custom domain is set, so expect a short wait before the first successful load.

## Keep in mind

- The flagship library stays at `github.com/yzhao062/pyod`. Moving it is not required:
  GitHub redirects any moved links, and the PyPI `pyod` package is independent of the
  repository location.
- Every claim on the page cites a verifiable source. Before wide sharing, confirm each
  adoption line still resolves to its record (careers pages and product docs move).
