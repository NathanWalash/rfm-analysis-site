# RFM Analysis — WordPress Theme

Custom WordPress **block theme** for `rfm-analysis.io`.  
This repository contains **only the theme** (no WordPress core, plugins, uploads, or database).

The theme ships with a landing-page template and reusable Patterns (hero, features, proof, pricing, contact) so you can assemble a marketing site quickly in the Site Editor.

---

## Requirements

- LocalWP: https://localwp.com
- Git
- WordPress 6.3+ (LocalWP “Preferred” stack is fine)

---

## Quick Start (LocalWP)

1) **Create a local site**
   - Open LocalWP → Create New Site → name it `rfm-analysis` → finish the wizard.

2) **Clone this theme into the local site's `themes` folder**  
   In LocalWP, right‑click your `rfm-analysis` site → **Show Folder**, then go to:
   ```
   app/public/wp-content/themes/
   ```

   Windows PowerShell:
   ```powershell
   cd "C:\Users\<you>\Local Sites\rfm-analysis\app\public\wp-content\themes"
   git clone https://github.com/NathanWalash/rfm-analysis-site.git rfm-analysis
   ```

   macOS/Linux:
   ```bash
   cd "$HOME/Local Sites/rfm-analysis/app/public/wp-content/themes"
   git clone https://github.com/NathanWalash/rfm-analysis-site.git rfm-analysis
   ```

3) **Activate the theme**
   - WP Admin → Appearance → Themes → Activate “RFM Analysis”.

4) **Create the Home page using the Landing template**
   - Pages → Add New → title it **Home**.
   - In the page settings sidebar, set **Template: Landing Page** → Publish.

5) **Make Home the front page and set permalinks**
   - Settings → Reading → “Your homepage displays” → **A static page** → **Home**.
   - Settings → Permalinks → **Post name**.

6) **Edit content**
   - Appearance → **Editor (Site Editor)**.
   - Edit **Templates → Page: Landing** to tweak the sections (hero, features, proof, pricing, contact).
   - Adjust header/footer under **Template Parts**. Insert or customize Patterns on any page.

---

## Repository Layout

The theme is at the repo root (flattened):

```
rfm-analysis/
├─ style.css                 # theme header (required by WordPress)
├─ theme.json                # global styles, colors, typography, layout
├─ templates/
│  ├─ index.html             # base template
│  └─ page-landing.html      # Landing Page template (used by Home)
├─ parts/
│  ├─ header.html            # site header with Navigation block
│  └─ footer.html            # site footer
└─ patterns/
   ├─ hero.php               # above-the-fold hero section
   ├─ features.php           # features grid
   ├─ proof.php              # social proof / metrics
   ├─ pricing.php            # pricing cards
   └─ contact.php            # contact block (replace shortcode if needed)
```

---

## Team Workflow

Both developers run LocalWP separately and work from the same Git repo.

### Cloning (each developer)
Clone the repo into your Local site's `wp-content/themes` as `rfm-analysis` (see Quick Start).  
Then activate the theme in wp-admin.

### Branching
Keep `main` stable; use feature branches for changes.

```bash
git checkout -b feat/hero
# edit files under the theme (templates, parts, patterns, theme.json, style.css)
git add .
git commit -m "feat(hero): initial hero pattern and copy"
git push -u origin feat/hero
# open a pull request, review, merge
git checkout main && git pull
```

### What lives in Git
- Theme code only: `style.css`, `theme.json`, `templates/**`, `parts/**`, `patterns/**`, and any other theme assets.
- Do not commit WordPress core, uploads, or the local database.

---

## Building Out Pages

Create the core pages from **Pages → Add New**: Home, Product, Pricing, Customers, About, Blog, Contact.

- For a blog index: Settings → Reading → set **Posts page** to **Blog**.
- Build navigation: Appearance → Editor → open **Template Parts → Header**, select the Navigation block, and add menu items (Home, Product, Pricing, Customers, About, Blog, Contact).

Use the provided Patterns (Insert → Patterns → rfm/*) to add hero, features, proof, pricing, and contact sections as needed.

---

## Plugins (install locally via wp-admin; not tracked in Git)

Keep plugin count lean during development.

- SEO: Yoast or Rank Math
- Forms: WPForms Lite or Fluent Forms
- Analytics: Site Kit (GA4) or Plausible
- Redirection: Redirection
- Media helper (optional): Enable Media Replace

Images: upload WebP where possible, ~1400px width for large hero screenshots, and provide alt text.

---

## Deployment (Ops)

1. Install WordPress on the target host.
2. Copy or deploy this theme to `wp-content/themes/rfm-analysis/` (or upload a ZIP of the repo).
3. Activate the theme in wp-admin.
4. Install required plugins (SEO, forms, analytics, redirection).
5. Create and select **Home** (Landing Page template) as the homepage, set **Permalinks → Post name**.
6. Optionally import starter content exports if provided (Tools → Import → WordPress).

---

## Troubleshooting

- **Landing Page template not available**  
  Ensure `templates/page-landing.html` exists in the active theme. Refresh the editor and check the page sidebar for the Template selector.

- **Sections not visible on Home**  
  Open Appearance → Editor → **Templates → Page: Landing**. Sections in the landing template are edited there (not in the page body).

- **Theme not appearing in Themes list**  
  Confirm the path:  
  `<site>/app/public/wp-content/themes/rfm-analysis/style.css`  
  and that `style.css` contains a valid WordPress theme header.

- **Cloned into wrong path**  
  If you see `themes/wp-content/themes/rfm-analysis`, delete the extra `wp-content` wrapper and reclone as shown in Quick Start.

- **Changes not updating**  
  Hard refresh the browser. Verify you are editing files in the active theme directory. Disable caching plugins locally.

---

## .gitignore (recommended)

Place this at the repo root to keep the theme clean:

```
# OS / editor
.DS_Store
Thumbs.db
.vscode/
.idea/
*.swp
*.swo
*.tmp

# Logs
*.log

# Env
.env
.env.*

# Node / build outputs (if you add a build step later)
node_modules/
dist/
build/
.cache/
*.map

# PHP / Composer (only if adopted later)
vendor/
composer.phar
composer.lock

# Archives
*.zip
```

---

## License

GPL-2.0-or-later (compatible with WordPress requirements).

