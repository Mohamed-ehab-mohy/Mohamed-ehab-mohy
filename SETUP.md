# ⚙️ Setup Guide — Activating Your GitHub Profile

This repository is a **GitHub profile README repo**. GitHub only turns a repo into your live profile page if the repo name **exactly matches your username**. Follow these steps once, in order, and everything (stats, snake, metrics) will run itself from then on.

---

## 1. Create the special repository

1. Go to GitHub and create a **new public repository** named exactly:
   ```
   Mohamed-ehab-mohy
   ```
2. Push the contents of this folder to that repo's `main` branch:
   ```bash
   git init
   git remote add origin https://github.com/Mohamed-ehab-mohy/Mohamed-ehab-mohy.git
   git add .
   git commit -m "feat: initial professional profile"
   git branch -M main
   git push -u origin main
   ```
3. Refresh `github.com/Mohamed-ehab-mohy` — your README should now render as your profile page.

---

## 2. Enable Actions permissions (needed for the snake + metrics workflows)

1. Go to **Settings → Actions → General** on the new repo.
2. Under **Workflow permissions**, select **"Read and write permissions"**.
3. Save.

---

## 3. Activate the contribution snake

The `snake.yml` workflow (in `.github/workflows/`) generates an animated snake that "eats" your contribution graph and publishes the SVG/GIF to a branch called `output`.

- No extra secrets are needed — it uses the built-in `GITHUB_TOKEN`.
- It runs automatically once a day, and also on every push to `main`.
- To trigger it manually the first time: go to **Actions → Generate Contribution Snake → Run workflow**.
- Once it runs once, the `output` branch will exist and the snake will show up in the README automatically (the README already points at `.../output/assets/snake-dark.svg`).

---

## 4. Activate the metrics panel (optional but recommended)

The `metrics.yml` workflow uses [`lowlighter/metrics`](https://github.com/lowlighter/metrics), which needs a **Personal Access Token (classic)** with `repo` and `read:user` scopes (the default token isn't enough for cross-repo language stats).

1. Create a token: **GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)** → scopes: `repo`, `read:user`.
2. In your **profile repo** → **Settings → Secrets and variables → Actions** → **New repository secret**:
   - Name: `METRICS_TOKEN`
   - Value: *(paste the token)*
3. Run the workflow manually once (**Actions → Generate Metrics → Run workflow**), then it will refresh every 12 hours.
4. If you'd rather skip this, you can safely delete `.github/workflows/metrics.yml` and the `assets/metrics.svg` reference — the README still works fully without it (stats/streak/langs/trophies don't need this token).

---

## 5. Double-check the dynamic image services

Everything else in the README (stats, streak, top languages, activity graph, trophies, summary cards, typing animation, quote box, profile-view counter) is powered by public, free services and needs **no setup** — they read live from your GitHub username automatically:

| Feature | Service |
|---|---|
| Typing animation | readme-typing-svg.demolab.com |
| Stats / Top Languages | github-readme-stats.vercel.app |
| Streak | streak-stats.demolab.com |
| Activity graph | github-readme-activity-graph.vercel.app |
| Trophies | github-profile-trophy.vercel.app |
| Summary cards | github-profile-summary-cards.vercel.app |
| Dynamic quote | quotes-github-readme.vercel.app |
| Profile views | komarev.com/ghpvc |

---

## 6. Repo pin cards for featured projects

The README embeds live repo cards for:
- `GymManagementSystem`
- `School-Portal-Docker-Microservices`
- `LibraryManagement-ProductionReady-Testing`

These cards pull the **real name, description, language, and star count directly from each repo** at render time. If any repo is renamed, made private, or doesn't exist yet, just update the `repo=` query parameter in `README.md` to match, or push the project so the card resolves.

---

## 7. Optional next steps

- Add a short GIF/screenshot to each featured project's own repository (not this one) — recruiters love seeing the UI.
- Pin `GymManagementSystem`, `School-Portal-Docker-Microservices`, and 4 more of your strongest repos via **Profile → Customize your pins**.
- Keep the "Currently working / learning" lines in `README.md` up to date — that's the section recruiters skim first.

You're done. 🎉
