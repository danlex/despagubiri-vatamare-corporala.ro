# despagubiri-vatamare-corporala.ro

Single-page Jekyll site for **Cabinet de Avocat VARZARU ION**, recreating the content of
`despagubiri-vatamare-corporala.ro` with a modern template inspired by `varzaru.ro`. Deployed on
GitHub Pages at the custom domain **despagubiri-vatamare-corporala.ro**.

## Structure

```
.
├── index.html              # Single page — assembles the section includes
├── _layouts/default.html   # HTML shell (head, header, footer, structured data)
├── _includes/              # Page sections
│   ├── header.html  footer.html
│   ├── hero.html  vatamare.html  servicii.html
│   ├── despre.html  afilieri.html  intrebari.html  testimoniale.html  contact.html
│   └── structured-data.html   # JSON-LD LegalService + FAQPage
├── assets/css/style.scss   # Theme (compiled to style.css by Jekyll)
├── assets/images/          # Logo, attorney photo, hero background, affiliation logos
├── _config.yml             # Site + contact + geo settings
├── confidentialitate.md termeni.md   # Legal pages
├── 404.html robots.txt llms.txt CNAME
└── .github/workflows/jekyll.yml   # Build + deploy to GitHub Pages
```

Editable content lives in the `_includes/*.html` section files. Contact details (phone, email, name)
and address are centralized in `_config.yml` and pulled in via `{{ site.contact.* }}` / `{{ site.geo.* }}`.

## Local preview

```bash
bundle install
bundle exec jekyll serve --livereload
# open http://localhost:4000
```

## Deploy (GitHub Pages)

1. Create a repo and push these files to the `main` branch.
2. In **Settings → Pages → Build and deployment**, set **Source = GitHub Actions**.
   (The included `.github/workflows/jekyll.yml` builds and deploys on every push to `main`.)
3. The `CNAME` file already sets the custom domain to `despagubiri-vatamare-corporala.ro`. In
   **Settings → Pages** confirm the custom domain and enable **Enforce HTTPS** once the certificate
   is issued.

## DNS (point the domain at GitHub Pages)

At your domain registrar / DNS host:

- **Apex `despagubiri-vatamare-corporala.ro`** → four `A` records:
  `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
  (optionally also the `AAAA` records: `2606:50c0:8000::153` … `8003::153`)
- **`www`** → `CNAME` to `<your-github-username>.github.io.`

DNS changes can take up to 24h to propagate; the HTTPS certificate is issued automatically afterwards.

## Notes on the rebuild

- The original site was a single static page (Bootstrap + LayerSlider theme) with a PHP contact form.
  The form posted to `contact.php`, which cannot run on GitHub Pages (static hosting), so it was
  replaced by direct **call / e-mail / WhatsApp** calls-to-action.
- All textual content (intro, attorney bio, the 5 Q&As, the 4 testimonials) was preserved from the
  original, with diacritics normalized.
- The firm's logo, attorney photo and affiliation marks are shared with the sibling site
  `avocat-asigurari-rca.ro`.
