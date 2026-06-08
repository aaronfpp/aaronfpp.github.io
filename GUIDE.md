# aaronfpp Project Guide

**Audience:** Future Copilot sessions, Aaron Hill, and incoming OSU FPP developers.
**Scope:** All public and private repositories under the `aaronfpp` GitHub account.
**Owner:** Oklahoma State University — Fire Protection Publications (OSU FPP).

---

## 1. Context

This account (`aaronfpp`) is the professional GitHub presence of Aaron Hill,
Systems Analyst at OSU Fire Protection Publications. It is not a personal
portfolio. All work product published here is OSU FPP property.

Projects are maintained for:
- Active internal use at OSU FPP
- Collaboration with current and future OSU FPP developers
- Professional reference and handoff

Personal and for-fun projects belong on a separate personal account.
Work-adjacent projects written on OSU equipment during break time should
be evaluated against OSU IP policy before publishing here.

---

## 2. Design System

All web-facing projects under this account follow the `aaronfpp` design system.

**Reference file:** `styleguide.html` (maintained in the `aaronfpp.github.io` repo)

Key tokens:

| Token | Value | Notes |
|---|---|---|
| `--hue` | `230` | Shift entire palette by changing this alone |
| `--chroma` | `0.06` | Saturation knob |
| `--primary` | `oklch(0.65 0.18 230)` | Brand blue — links, CTAs, highlights |
| `--bg-dark` | `oklch(0.14 ...)` | Page background |
| `--font-sans` | Manrope | Body and UI text |
| `--font-mono` | JetBrains Mono | Code, tokens, repo names |

Import fonts from Google Fonts:

```html
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet" />
```

Do not introduce new fonts, color systems, or component libraries without
updating the style guide first.

---

## 3. Naming Conventions

| Type | Convention | Examples |
|---|---|---|
| Repo names | camelCase | `imageScraper`, `heatWave` |
| Multi-word repos | camelCase, no separators | `imageScraperExt` |
| Deployment branches | `main` | Always |
| Config variables in JS | SCREAMING_SNAKE_CASE | `GITHUB_USER`, `CACHE_TTL` |
| CSS custom properties | kebab-case with `--` prefix | `--bg-dark`, `--font-mono` |
| File names | camelCase for scripts, kebab for assets | `loadRepos.js`, `apple-touch-icon.png` |

---

## 4. Project Initialization Checklist

Complete in order when creating a new repository.

### 4a. On GitHub

- [ ] Create the repo under `aaronfpp` (not a personal account)
- [ ] Set visibility intentionally — see Section 5
- [ ] Add a clear one-line description in the repo Settings
- [ ] Set the Homepage field if the project has a live deployment
- [ ] Do not add a license without OSU FPP approval

### 4b. In the Repository

- [ ] Initialize with a `README.md` — use the template in Section 7
- [ ] Add the OSU FPP ownership comment block — see Section 8
- [ ] Add a `.gitignore` appropriate to the language
- [ ] If web-based: apply the design system from the style guide
- [ ] If Python: include a `requirements.txt`
- [ ] If Node: include a `package.json` with a meaningful `description` field

### 4c. Deployment (if applicable)

- [ ] Target: GitHub Pages from `main` branch root (no build step preferred)
- [ ] Confirm the live URL and set it as the repo Homepage field on GitHub
- [ ] Test on mobile — all projects use responsive layouts by default

---

## 5. Public vs. Private Decision Criteria

Default to **private**. Make public only when all of the following are true:

- The project is functional and not in an embarrassing early state
- It contains no credentials, internal URLs, or OSU FPP internal references
- It has a complete README (Section 7)
- It has the OSU FPP ownership block (Section 8)
- It has no license file, or a license has been approved by OSU FPP

**Always private:**
- Backend workers, proxies, or services with API keys
- Experimental or test repos not intended for outside eyes
- Anything containing internal OSU systems references

**Candidates for public:**
- Standalone web tools with no backend secrets
- Scripts useful to future FPP developers
- Completed projects ready for handoff

---

## 6. Contributor Attribution

When a project originates from or significantly incorporates work by another
contributor (student worker, contractor, collaborator), credit them explicitly
in the README.

Standard format:

```markdown
## Attribution

Original implementation by [First Last](https://github.com/username),
[role] at OSU Fire Protection Publications.
This version extends the original with [brief description of changes].
```

Do not obscure or omit prior authorship. OSU FPP IP ownership of the work
product is separate from crediting the individuals who wrote it.

---

## 7. README Template

Copy this block into every new repo. Fill in all bracketed sections.

```markdown
# [repo-name]

[One sentence: what it does and why it exists.]

---

## Overview

[Two to four sentences describing the problem it solves, who uses it,
and how it fits into OSU FPP operations.]

## Requirements

[List runtime dependencies, environment requirements, or prerequisites.
Delete this section if not applicable.]

## Usage

[How to run, install, or deploy. Include commands where relevant.
Delete this section if not applicable.]

## Status

[Active | Complete | Archived] — [one sentence on current state and
any known limitations or planned work.]

## Attribution

[Credit prior authors if applicable — see Section 6. Delete if sole author.]

---

> All work product in this repository is property of
> Oklahoma State University — Fire Protection Publications (OSU FPP).
```

---

## 8. OSU FPP Ownership Block

Include in every repository, in the format appropriate to the file type.

**HTML (in `<head>`, before all other content):**

```html
<!--
  OSU Fire Protection Publications
  All work product and content in this repository is property of
  Oklahoma State University — Fire Protection Publications (OSU FPP).
-->
```

**JavaScript / Python (top of file):**

```js
// OSU Fire Protection Publications
// All work product in this file is property of
// Oklahoma State University — Fire Protection Publications (OSU FPP).
```

```python
# OSU Fire Protection Publications
# All work product in this file is property of
# Oklahoma State University — Fire Protection Publications (OSU FPP).
```

**README (bottom, as blockquote):**

```markdown
> All work product in this repository is property of
> Oklahoma State University — Fire Protection Publications (OSU FPP).
```

This block is not a license. It is an ownership attribution. Do not add
a `LICENSE` file without explicit OSU FPP approval.

---

## 9. Deployment Notes

### GitHub Pages (standard)

All web projects deploy from `main` branch root. No build step.

Enable once per repo:
**Settings → Pages → Source → Deploy from branch → `main` / `/ (root)`**

The landing page (`aaronfpp.github.io`) is fully dynamic — it reads
public repos from the GitHub API automatically. No changes to
`index.html` are needed when adding or removing projects. Control is
handled entirely through GitHub repo settings:

| GitHub action | Effect on landing page |
|---|---|
| Make repo public | Card appears |
| Make repo private | Card disappears |
| Set Homepage field | Live badge + Live button appear |
| Archive repo | Archived badge appears |

### Favicon Pack

All deployed web projects should include the standard aaronfpp favicon pack.
Reference `aaronfpp.github.io` for the current asset set and `site.webmanifest`.

Standard `<head>` favicon block:

```html
<link rel="icon" type="image/x-icon"            href="/favicon.ico" />
<link rel="icon" type="image/png" sizes="96x96" href="/favicon-96x96.png" />
<link rel="apple-touch-icon"                    href="/apple-touch-icon.png" />
<link rel="manifest"                            href="/site.webmanifest" />
<meta name="theme-color" content="#1a1d2e" />
```

---

## 10. Update and Maintenance Checklist

Run through this when revisiting an existing project.

- [ ] Is the README still accurate? Update if status, usage, or ownership has changed
- [ ] Is the repo visibility still correct? Re-evaluate against Section 5
- [ ] Are dependencies current? Check for security notices
- [ ] If web-based: does it still match the design system?
- [ ] Is the OSU FPP ownership block present in all relevant files?
- [ ] If the project is complete and will not be actively maintained: archive it on GitHub

---

## 11. Working with Copilot

When starting a new session involving this account or its projects, provide
this guide as context. Copilot should:

- Plan and ask questions regarding loose ends before starting work
- Produce no emojis unless explicitly asked
- Default to the aaronfpp design system for all web output
- Apply the README template and ownership block to all new files
- Flag any action that could conflict with OSU IP policy
- Keep responses direct and without unnecessary filler

---

*This guide is maintained in `aaronfpp.github.io/GUIDE.md`.*
*Last revised: June 2026.*
