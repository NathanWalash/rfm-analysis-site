# RFM Analysis — WordPress Theme

Custom WordPress **block theme** for `rfm-analysis.io`.  
This repo contains **only the theme** (no WordPress core, plugins, uploads, or DB).

Sections provided as reusable Patterns: hero, features, proof, pricing, contact.

---

## Requirements

- LocalWP: https://localwp.com
- Git
- WordPress 6.3+ (LocalWP “Preferred” stack is fine)

---

## Quick Start (LocalWP)

1. **Create a local site**
   - LocalWP → **Create New Site** → name it `rfm-analysis` → finish the wizard.

2. **Clone this theme into the site’s `themes` folder**

   In LocalWP, right-click your `rfm-analysis` site → **Show Folder**, then go to:
   ```
   app/public/wp-content/themes/
   ```

   **Windows PowerShell**
   ```powershell
   cd "C:\Users\<you>\Local Sites\rfm-analysis\app\public\wp-content\themes"
   git clone https://github.com/NathanWalash/rfm-analysis-site.git rfm-analysis
   ```

   **macOS/Linux**
   ```bash
   cd "$HOME/Local Sites/rfm-analysis/app/public/wp-content/themes"
   git clone https://github.com/NathanWalash/rfm-analysis-site.git rfm-analysis
   ```

3. **Activate the theme**
   - WP Admin → **Appearance → Themes** → **Activate “RFM Analysis.”**

4. **Set homepage and permalinks**
   - Pages → **Add New** → create **Home**.
   - In the page sidebar, set **Template: Landing Page** → Publish.
   - Settings → **Reading** → “Your homepage displays” → **A static page** → **Home**.
   - Settings → **Permalinks** → **Post name**.

5. **Start building**
   - Appearance → **Editor (Site Editor)** to edit templates, header/footer, and insert theme Patterns.

---

## Repository Layout

The theme lives at the repo root (flattened):

```
rfm-analysis/
├─ style.css
├─ theme.json
├─ templates/
│  ├─ index.html
│  └─ page-landing.html
├─ parts/
│  ├─ header.html
│  └─ footer.html
└─ patterns/
   ├─ hero.php
   ├─ features.php
   ├─ proof.php
   ├─ pricing.php
   └─ contact.php
```

- `style.css` — theme header (makes WP recognize the theme).
- `theme.json` — global colors/typography/layout.
- `templates/` — page templates (base + landing).
- `parts/` — header/footer template parts.
- `patterns/` — reusable content sections for fast page building.

---

## Dev Workflow

- Clone this repo into your Local site’s `wp-content/themes/` as `rfm-analysis`.
- Create feature branches, then open PRs:
  ```bash
  git checkout -b feat/hero
  git add .
  git commit -m "feat(hero): initial hero pattern"
  git push -u origin feat/hero
  ```
- After PR merge:
  ```bash
  git checkout main
  git pull
  ```
- Keep plugins lean during development (install via wp-admin; not tracked in Git):
  - SEO: Yoast or Rank Math
  - Forms: WPForms Lite or Fluent Forms
  - Analytics: Site Kit (GA4) or Plausible
  - Redirection
  - Enable Media Replace (optional)

### Sharing starter content (optional)
- Tools → **Export** → *All content* → save the XML under `/content-seed/` in this repo.
- Teammate: Tools → **Import → WordPress** to import the XML.

---

## Deployment (Ops)

1. Install WordPress on the target host.
2. Copy this theme to `wp-content/themes/rfm-analysis/` (or upload a ZIP).
3. Activate the theme in wp-admin.
4. Install required plugins (SEO, forms, analytics, redirection).
5. Set **Home** as the homepage and **Permalinks → Post name**.
6. Optionally import `/content-seed/*.xml`.

---

## Troubleshooting

- **Theme not visible**  
  Ensure the path is exactly:
  ```
  <site>/app/public/wp-content/themes/rfm-analysis/style.css
  ```
  and `style.css` contains a valid WordPress theme header.

- **Cloned into the wrong path**  
  If you see `themes/wp-content/themes/rfm-analysis`, delete the extra `wp-content` wrapper and reclone as shown in Quick Start.

- **Changes not appearing**  
  Hard-refresh the browser, confirm you’re editing files in the active theme folder, and check for caching plugins (disable locally).

---

## License

GPL-2.0-or-later (compatible with WordPress requirements).
