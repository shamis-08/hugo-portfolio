# Hugo Portfolio Starter (PaperMod)

This repo is a minimal Hugo site configured for GitHub Pages deployment with PaperMod.

## Quickstart

```bash
# 1) Create repo & clone
git clone https://github.com/shamis-08/hugo-portfolio.git
cd hugo-portfolio

# 2) Copy these files into the repo (or download the ZIP from ChatGPT and unzip here)

# 3) Init git and add PaperMod theme as submodule
git init
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git add .
git commit -m "Init Hugo site with PaperMod"

# 4) Push
git branch -M main
git remote add origin https://github.com/shamis-08/hugo-portfolio.git
git push -u origin main

# 5) Enable GitHub Pages in repo Settings -> Pages -> Build and deployment -> Source: GitHub Actions
```

## Local run

```bash
brew install hugo  # or grab a binary from https://gohugo.io
hugo server -D
```

Edit content in `content/` and configure options in `hugo.toml`.
