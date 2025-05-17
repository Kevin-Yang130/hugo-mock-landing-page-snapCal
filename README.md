# Hugo Mock Landing Page for SnapCal

A **simple and clean Hugo-based landing page** tailor-made for **SnapCal** — an app that uses image recognition to estimate the calorie content of food. This lightweight starter puts your product's core message at the forefront, while offering easy customization, responsive design, and SEO-friendly structure. Perfect for getting a polished, professional presence online in no time.

🔗 **[Check out the live demo here](https://your-demo-link.github.io)** <!-- Replace with actual demo link if available -->

---

## ⚙️ GitHub Actions Deployment Workflow

This project includes a GitHub Actions workflow located at `.github/workflows/gh-pages-deployment.yaml`. The workflow:

- Automatically builds the Hugo site
- Deploys the generated static content to GitHub Pages
- Is triggered on every push to the `main` branch

The deployment uses the [`peaceiris/actions-gh-pages`](https://github.com/peaceiris/actions-gh-pages) action to handle publishing. This removes the need for manual deployments and ensures the site stays up to date with every commit.

### 📝 Example Workflow Summary

```yaml
name: GitHub Pages Deployment

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: '0.123.7'
      - name: Build
        run: hugo --minify
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
