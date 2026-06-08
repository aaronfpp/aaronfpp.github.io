# aaronfpp.github.io

Public project navigator for [Aaron Hill](https://github.com/aaronfpp) \u2014
Systems Analyst, Oklahoma State University Fire Protection Publications.

**Live \u2192** https://aaronfpp.github.io

---

## How cards are controlled

Cards are pulled live from the GitHub API. No edits to this file are needed
to add or remove a project \u2014 just manage your repos on GitHub.

| What you do on GitHub | What appears on the site |
|---|---|
| Make a repo public | Card appears automatically |
| Set **Homepage** in repo Settings | Card shows a **Live \u2197** button and a green **Live** badge |
| Archive a repo | Card shows a muted **Archived** badge |
| Make a repo private | Card disappears automatically |

The following repos are always excluded from the card list regardless of
visibility: `aaronfpp` (profile README) and `aaronfpp.github.io` (this site).

---

## Sort order & config

Open `index.html` and edit the `<script>` block near the top of `<head>`:

```js
const GITHUB_USER   = 'aaronfpp';
const SORT          = 'updated';   // 'updated' | 'stars' | 'created'
const EXCLUDE_FORKS = true;
```

---

## Deployment

Served via **GitHub Pages** from the `main` branch root. No build step.

Enable once: **Settings \u2192 Pages \u2192 Source \u2192 Deploy from branch \u2192 `main` / `/ (root)`**

---

> All work product and content in this repository is property of
> Oklahoma State University \u2014 Fire Protection Publications (OSU FPP).
