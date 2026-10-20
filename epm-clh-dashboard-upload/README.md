# EPM to CLH: features needed by database

A dashboard that shows why building one feature doesn't move EPM databases to CLH. A database can migrate only when every feature it relies on exists in CLH, and most databases need several.

All files sit in one folder so they can be uploaded to GitHub in a single step.

## Files

| File | What it is |
|---|---|
| `index.html` | The dashboard page |
| `dashboard-data.js` | Data loaded by `index.html` (built from the Client Directory) |
| `build_data.py` | Rebuilds `dashboard-data.js` from a new Client Directory workbook |
| `requirements.txt` | Python package needed by `build_data.py` |
| `favicon.svg` | Browser tab icon |
| `tiempos-text-regular.woff2`, `tiempos-text-regular-italic.woff2`, `national-2-regular.woff2`, `national-2-bold.woff2` | Elsevier brand fonts |
| `.nojekyll` | Tells GitHub Pages to serve files as-is |
| `robots.txt` | Asks search engines not to index the site |
| `.gitignore` | Keeps workbooks and temporary files out of the repository |
| `README.md` | This file |

## What the dashboard shows

1. Executive summary
2. At a glance (with why some databases aren't blocked by functionality)
3. Build simulator
4. Features needed
5. Databases by selected feature (CSV export)
6. Databases sorted by features needed (grouped by account; CSV export)
7. How we counted (with glossary)
8. Why we count databases, not customers

## Set up a new repository

1. In GitHub, choose **New repository**. Give it a name, set it to **Private**, and leave "Add a README" unticked. Click **Create repository**.
2. On the empty repository page, click **uploading an existing file**.
3. Drag in **all the files** from this folder (select them with Ctrl+A; drag the files, not the folder). In File Explorer, turn on **View → Show → Hidden items** first so `.nojekyll` and `.gitignore` are included.
4. Click **Commit changes**.
5. Go to **Settings → Pages**. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose **main** and **/ (root)**, and click **Save**.
6. Wait 1 to 2 minutes, then refresh the Pages settings page. The site address appears at the top (usually `https://<your-account>.github.io/<repository-name>/`).
7. Open the address. The small "Page version" line above the disclaimer confirms you're seeing the latest upload.

If your organization supports it, set Pages visibility to **Private** in the same settings page.

**Before you publish:** the data file contains account names, IDs, contract values and learner counts. On most GitHub plans a Pages site is public even if the repository is private. Confirm with your data owner, or use private Pages.

## Updating the data

1. Save the latest Client Directory workbook locally. Don't upload it (workbooks are in `.gitignore`).
2. In this folder, run:

   ```
   pip install -r requirements.txt
   python build_data.py "path/to/Client Directory.xlsx"
   ```

3. Upload the new `dashboard-data.js` to the repository (replace the old one). The site updates automatically.

## Editing text

Open the dashboard, click **Edit text** (bottom right), make changes, then **Save edited copy** and upload the downloaded file in place of `index.html`.

## Contact

Tessa Richards, Customer Readiness Manager (t.richards@elsevier.com)
