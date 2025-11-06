# Hugo Portfolio Starter (PaperMod)

## Quickstart

```bash
# 1) Создаем репозиторий и клонируем его 
git clone https://github.com/shamis-08/hugo-portfolio.git
cd hugo-portfolio

# 2) Копируем файлы в репозиторий

# 3) Инициализируем git и добавляем тему PaperMod как подмодуль
git init
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git add .
git commit -m "Init Hugo site with PaperMod"

# 4) Пушим
git branch -M main
git remote add origin https://github.com/shamis-08/hugo-portfolio.git
git push -u origin main

# 5) Включаем GitHub Pages в разделе Settings -> Pages -> Build and deployment -> Source: GitHub Actions
```
