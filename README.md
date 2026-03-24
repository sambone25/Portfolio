# Portfolio — Your Name

![CI/CD](https://github.com/sambone25/Portfolio/actions/workflows/ci.yml/badge.svg)
![GitHub Pages](https://img.shields.io/badge/live-GitHub%20Pages-blue)

Personal portfolio site for a Backend / DevOps engineer. Plain HTML/CSS/JS served by nginx in Docker, with a full GitHub Actions CI/CD pipeline.

## Pipeline

```
git push to main
      │
      ▼
┌─────────────┐
│  1. Lint    │  HTMLHint · Prettier · Stylelint
└──────┬──────┘
       │ needs: lint
       ▼
┌─────────────┐
│  2. Validate│  W3C HTML check · link checker
└──────┬──────┘
       │ needs: validate
       ▼
┌─────────────┐
│  3. Build   │  Docker + nginx · smoke test curl /
└──────┬──────┘
       │ needs: build · main only
       ▼
┌─────────────┐
│  4. Deploy  │  GitHub Pages auto-deploy
└─────────────┘
```

## Local development

```bash
# Open directly
open index.html

# Or run in Docker
docker build -t portfolio .
docker run -p 8080:80 portfolio
# → http://localhost:8080
```

## Customising

| What                | Where                          |
|---------------------|--------------------------------|
| Your name & bio     | `index.html` — hero section    |
| Photo               | Replace `div.photo-placeholder` with `<img src="assets/photo.jpg">` |
| Skills              | `index.html` — skills section  |
| Projects            | `index.html` — projects section |
| Links               | `index.html` — hero + contact  |
| Colors / fonts      | `style.css` — `:root` vars     |

## Setup (first time)

1. Create a public GitHub repo
2. Push this code to `main`
3. Go to **Settings → Pages → Source → gh-pages branch**
4. Replace `YOUR_USERNAME` / `YOUR_REPO` in this README with your real values
5. Your live site: `https://YOUR_USERNAME.github.io/YOUR_REPO`
