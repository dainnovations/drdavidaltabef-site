# drdavidaltabef.com — static site

Plain HTML/CSS, no build step. Seven pages: `index.html`, `coaching.html`, `therapy.html`, `workshops.html`, `consulting.html`, `about.html`, `contact.html`, plus `styles.css` and `assets/`.

## One thing to do before launch

Both forms (contact page + workshop interest list) post to Formspree. Create a free account at [formspree.io](https://formspree.io), add a form pointing at **david@drdavidaltabef.com**, and replace `YOUR_FORM_ID` in **contact.html** and **workshops.html** with the real form ID (it appears twice total). Until then, form submissions won't go anywhere.

## Deploying to GitHub Pages

1. Create a new **public** GitHub repo (e.g. `drdavidaltabef-site`).
2. Upload all files so `index.html` sits at the repo root (the GitHub web UI works fine — no git required).
3. Repo Settings → Pages → Deploy from a branch → `main` / `(root)`. Verify the site at `https://<username>.github.io/drdavidaltabef-site/`.

## Pointing drdavidaltabef.com at it (Cloudflare)

1. GitHub Pages settings → Custom domain: `drdavidaltabef.com`. Also verify the domain in your GitHub account settings.
2. In Cloudflare DNS: remove the Squarespace records (A records to 198.185.159.x / 198.49.23.x, and the `www` CNAME to Squarespace). Add A records for `@` → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153, and a CNAME `www` → `<username>.github.io`. Set these to **DNS only (grey cloud)** so GitHub can issue the SSL certificate.
3. When the DNS check passes in GitHub Pages settings, enable **Enforce HTTPS** (the certificate can take up to an hour).
4. Test both `drdavidaltabef.com` and `www.` in a private window, then — and only then — disconnect the domain in Squarespace and cancel the subscription.

## Editing later

Edit the HTML files directly in the GitHub repo (the web editor is fine); changes go live in about a minute. `build.py` is an optional authoring helper that regenerates all seven pages with a shared nav/footer — you don't need it to deploy or make small edits.
