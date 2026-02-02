# GitHub Pages Publishing Review: Transform to Open Science

## Current Status

✅ **The repository is ALREADY configured for GitHub Pages publishing!**

Your project is actively using GitHub Pages to host the website at: [https://nasa.github.io/Transform-to-Open-Science/](https://nasa.github.io/Transform-to-Open-Science/)

---

## Current Setup Overview

### 1. **Build Tool: Jupyter Book**
- The site is built using [Jupyter Book](https://jupyterbook.org/), an open-source tool that converts markdown/notebook files into a beautiful HTML website
- Located in the root directory with source files in markdown format

### 2. **Deployment Workflow**
**File:** `.github/workflows/book.yml`

The GitHub Actions workflow handles:
- **Trigger:** Pushes to the `website` branch automatically trigger the build
- **Build Process:**
  - Sets up Python 3.9
  - Installs dependencies from `book-requirements-Linux-macOS.txt`
  - Runs `jupyter-book build .` to generate HTML
- **Publishing:**
  - Uses `peaceiris/actions-gh-pages@v3` action
  - Publishes to the `gh-pages` branch
  - Automatically updates the live website

### 3. **Branch Structure**
- **`website` branch:** Source files (markdown, configuration, content)
- **`gh-pages` branch:** Generated HTML (automatically created and updated by GitHub Actions)

---

## What's Working Well ✅

1. **Automated Deployment** - Changes pushed to the `website` branch automatically build and deploy
2. **Professional Documentation** - Well-organized markdown files across 4 main content areas
3. **Jupyter Book Configuration** - Appears to have working build dependencies
4. **GitHub Actions CI/CD** - Efficient workflow using standard tooling
5. **Clean Content Structure** - Organized folders for Engagement, Capacity Sharing, Incentives, and Moving to Openness
6. **Code of Conduct & Contributing Guidelines** - Professional community standards
7. **All Contributors Badge** - Community recognition integrated

---

## Issues & Recommendations

### 🔴 **Critical Issues to Address**

#### 1. **Missing Jupyter Book Configuration Files**
The build expects:
- `book-requirements-Linux-macOS.txt` - NOT FOUND
- `_config.yml` - Jupyter Book configuration - NOT FOUND
- `_toc.yml` - Table of contents - NOT FOUND

**Impact:** The `jupyter-book build` command will fail without these files.

**Solution:**
```bash
# You need to create these files. Minimal example:

# _config.yml
title: Transform to Open Science
author: NASA TOPS
format: jb-book

# _toc.yml
format: jb-book
chapters:
- file: README.md
- file: docs/Area1_Engagement/readme.md
  sections:
    - file: docs/Area1_Engagement/contactus.md
    # ... add other files
```

#### 2. **Broken Link Check Workflow is Incomplete**
**File:** `.github/workflows/broken-link-check.yml`

The URL is a placeholder: `url: "https://..."` 

**Solution:** Update to your actual site:
```yaml
url: "https://nasa.github.io/Transform-to-Open-Science/"
```

### 🟡 **Recommended Improvements**

1. **Add a Deployment Status Badge** - Show visitors the current build status in README
   ```markdown
   ![Deploy Book](https://github.com/nasa/Transform-to-Open-Science/actions/workflows/book.yml/badge.svg?branch=website)
   ```

2. **GitHub Pages Settings** - Verify in your repository settings:
   - Settings → Pages
   - Source: Deploy from a branch
   - Branch: `gh-pages` / `root`

3. **Add Custom Domain (Optional)** - If you own a domain:
   - Add CNAME file to root: `Transform-to-Open-Science`
   - Configure in Settings → Pages

4. **Enhanced Workflows:**
   - Add link checking on pull requests (before merge)
   - Add spell-check validation
   - Add build preview for PRs

5. **Documentation** - Add to your CONTRIBUTING.md:
   - How to run `jupyter-book build` locally
   - Preview instructions
   - Git workflow (push to `website` branch for deployment)

---

## Quick Start to Fix & Deploy

### Step 1: Create Jupyter Book Config Files

Create `_config.yml`:
```yaml
# Book settings
title: Transform to Open Science
author: NASA TOPS
logo: https://zenodo.org/record/7742997/files/Tops_Badge_Nasa.png

format: jb-book
options:
  numbered: false
  
html:
  home_page_in_navbar: true
  use_issues_button: true
  use_repository_button: true
```

Create `_toc.yml`:
```yaml
format: jb-book
chapters:
- file: README.md
- file: docs/Area1_Engagement/readme.md
  title: Area 1 - Engagement
- file: docs/Area2_Capacity_Sharing/readme.md
  title: Area 2 - Capacity Sharing
- file: docs/Area3_Incentives/readme.md
  title: Area 3 - Incentives
- file: docs/Area4_Moving_To_Openness/readme.md
  title: Area 4 - Moving to Openness
```

### Step 2: Create Requirements File

Create `book-requirements-Linux-macOS.txt`:
```
jupyter-book==0.15.1
jupyterlab==4.0.9
matplotlib==3.8.2
numpy==1.24.3
pandas==2.1.3
scipy==1.11.4
```

### Step 3: Fix GitHub Workflow

Update `.github/workflows/broken-link-check.yml`:
```yaml
url: "https://nasa.github.io/Transform-to-Open-Science/"
```

### Step 4: Deploy

```bash
git add _config.yml _toc.yml book-requirements-Linux-macOS.txt
git commit -m "Add Jupyter Book configuration files"
git checkout website  # Switch to website branch
git merge main        # Or your primary branch
git push origin website
```

The GitHub Actions workflow will automatically:
1. ✅ Build the site
2. ✅ Generate HTML in `./_build/html`
3. ✅ Push to `gh-pages` branch
4. ✅ Update your live website

---

## Deployment Checklist

- [ ] Create `_config.yml` with Jupyter Book settings
- [ ] Create `_toc.yml` with proper table of contents
- [ ] Create `book-requirements-Linux-macOS.txt` with Python dependencies
- [ ] Fix broken-link-check.yml URL
- [ ] Commit and push to `website` branch
- [ ] Verify GitHub Actions workflow runs successfully
- [ ] Check live site at https://nasa.github.io/Transform-to-Open-Science/
- [ ] Add deployment badge to README.md
- [ ] Update CONTRIBUTING.md with local preview instructions
- [ ] Test links and navigation

---

## Reference Links

- [Jupyter Book Documentation](https://jupyterbook.org/)
- [GitHub Pages Setup Guide](https://docs.github.com/en/pages/getting-started-with-github-pages)
- [GitHub Actions for Pages](https://github.com/peaceiris/actions-gh-pages)
- [Your Live Site](https://nasa.github.io/Transform-to-Open-Science/)

