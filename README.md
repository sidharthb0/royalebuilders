# Royale Builders & Developers — Website

A clean, minimalistic, luxury real estate website with CMS-powered content management.

## Quick Start

### 1. Deploy to GitHub Pages

1. Go to **Settings → Pages** in this repository
2. Under "Source", select **Deploy from a branch** → **main** → **/ (root)**
3. The site will deploy automatically on every push

### 2. Custom Domain Setup

1. In **Settings → Pages → Custom domain**, enter `royalebuilders.com`
2. Add these DNS records at your domain registrar:

   | Type  | Name | Value                          |
   |-------|------|--------------------------------|
   | CNAME | www  | sidharthb0.github.io           |
   | A     | @    | 185.199.108.153                |
   | A     | @    | 185.199.109.153                |
   | A     | @    | 185.199.110.153                |
   | A     | @    | 185.199.111.153                |

3. Check "Enforce HTTPS" once DNS propagates

### 3. Content Management (CMS)

#### Recommended: Sveltia CMS (No OAuth Server Needed)

1. In `admin/index.html`, replace the script tag with:
   ```html
   <script src="https://unpkg.com/@sveltia/cms/dist/sveltia-cms.js"></script>
   ```
2. In `admin/config.yml`, simplify the backend to:
   ```yaml
   backend:
     name: github
     repo: sidharthb0/royalebuilders.com
     branch: main
   ```
3. Visit `royalebuilders.com/admin` and sign in with GitHub

#### Alternative: Decap CMS with Netlify Identity

1. Create a free Netlify site connected to this repo
2. Enable Netlify Identity + Git Gateway in Netlify dashboard
3. Visit `royalebuilders.com/admin` and sign in

### 4. Contact Form (Formspree)

1. Create a free account at [formspree.io](https://formspree.io)
2. Create a new form and copy the form ID (e.g., `xabcdefg`)
3. Update via CMS: **Site Settings → Form Settings → Formspree Form ID**
4. Or edit `_data/settings.json` directly

### 5. Adding Content

#### Via CMS (recommended)
- Go to `royalebuilders.com/admin`
- Add/edit Projects, Team Members, or Site Settings
- Changes are committed to GitHub and auto-deploy

#### Via code
- **Projects:** Add a JSON file to `_data/projects/`
- **Team:** Add a JSON file to `_data/team/`
- **Settings:** Edit `_data/settings.json`
- The GitHub Action auto-updates `_data/manifest.json`

### 6. Replacing Placeholder Images

Upload your images via the CMS media library, or place them in `images/uploads/` and reference them in the JSON files.

## File Structure

```
├── index.html              # Main site
├── admin/
│   ├── index.html          # CMS admin panel
│   └── config.yml          # CMS configuration
├── _data/
│   ├── settings.json       # Site settings (contact, about, stats)
│   ├── manifest.json       # Auto-generated file list
│   ├── projects/           # One JSON per project
│   └── team/               # One JSON per team member
├── images/uploads/         # CMS-uploaded media
└── .github/workflows/      # Auto-manifest generator
```
