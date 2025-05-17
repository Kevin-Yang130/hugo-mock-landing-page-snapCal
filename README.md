# Hugo Mock Landing Page for SnapCal

A **clean, minimal Hugo-based landing page** built for **SnapCal** — an app that estimates the calorie content of food using image recognition. This project focuses on clarity, responsiveness, and ease of customization. It’s ideal for showcasing a product with a polished, SEO-friendly web presence.

🔗 **[Live Demo](https://your-username.github.io/hugo-mock-landing-page-autodeployed/)** <!-- Replace with actual GitHub Pages URL -->

---

## ⚙️ GitHub Actions Deployment Workflow

This repository uses GitHub Actions to automatically **build and deploy** the Hugo site to **GitHub Pages** whenever changes are pushed to the `main` branch.

The workflow file is located at `.github/workflows/gh-pages-deployment.yaml` and consists of the following steps:

### 🧱 Workflow Summary

- **Trigger:** Push to `main` branch  
- **Checkout:** Clones the repo and pulls submodules (for themes)  
- **Hugo Setup:** Installs Hugo v0.144.1 with extended features  
- **Build:** Compiles the Hugo site with draft content, garbage collection, and minification  
- **Deploy:** Publishes the `public` folder to the `gh-pages` branch using `peaceiris/actions-gh-pages`

### 📄 Sample Workflow

```yaml
name: 🏗️ Build and Deploy GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-22.04
    steps:
      - name: 🔄 Check Out Source Repository
        uses: actions/checkout@v3.5.1
        with:
          submodules: true
          fetch-depth: 0

      - name: 🛠️ Initialize Hugo Environment
        uses: peaceiris/actions-hugo@v2.6.0
        with:
          hugo-version: "0.144.1"
          extended: true

      - name: 🏗️ Compile Hugo Static Files
        run: hugo -D --gc --minify

      - name: 🚀 Publish to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3.9.3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_branch: gh-pages
          user_name: "github-actions[bot]"
          user_email: "github-actions[bot]@users.noreply.github.com"
