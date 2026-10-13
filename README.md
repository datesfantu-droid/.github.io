# DELTA-Hub Support – project website

Website of the UEFISCDI-funded project (Premiere Orizont Europa – Instituții) supporting
DELTA-Hub at the University of Bucharest. Published at <https://dh-suport.unibuc.ro>.

Built with [MkDocs](https://www.mkdocs.org/) and [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/).
Pages are generated at build time from Markdown – no JavaScript is needed to show content.

## Where things live

| What | File |
|---|---|
| Key project facts (title, numbers, budget, director, contact) | `data/project.yml` – single source of truth, used by every page |
| Pages | `docs/*.md` |
| Events / news | `docs/events/posts/YYYY-MM-DD-short-title.md` – picked up automatically |
| Photos | `docs/assets/images/` |
| Logo, styles | `docs/assets/` |
| Funding banner shown on every page | `overrides/main.html` |

## Keeping the site compliant

Financing contract art. 6.1.26 requires the site to stay up to date with: project summary, team,
publications, main results and their cognitive and socio-economic impact. After each report, update:

- `docs/reports.md` – results for the completed stage, with 2–3 photos;
- `docs/results.md` and `docs/publications.md`;
- `docs/team.md` when the team changes;
- a new post in `docs/events/posts/` for every event.

## Adding an event

Create `docs/events/posts/2026-11-20-workshop.md`:

```markdown
---
date: 2026-11-20
categories:
  - Workshop
---

# Remote sensing workshop

Short summary shown in the list.

<!-- more -->

Full description, photos…
```

## Local development

```bash
pip install -r requirements.txt
mkdocs serve        # http://127.0.0.1:8000
```

## Deployment

Every push to `main` builds the site and deploys it to GitHub Pages
(`.github/workflows/deploy.yml`). In the repository settings, set
**Pages → Build and deployment → Source** to **GitHub Actions**.
