# Data Learning Program

A personal, self-paced program to learn **databases**, **data engineering** and **data analytics**,
published as a website with GitHub Pages.

The site is the program: every module page has goals, resources, exercises, a mini-project
and a "done when" checklist. The repo also holds my progress tracker, weekly learning log and
project work.

## Layout

| Path | What it is |
| --- | --- |
| `index.md` | Home page: what the program is and how to use it |
| `program/` | Roadmap, learning principles, progress tracker, resource library |
| `tracks/00-setup.md` | Phase 0: tooling and habits |
| `tracks/databases/` | Phase 1: SQL, data modeling, internals, transactions |
| `tracks/data-engineering/` | Phase 2: files and formats, pipelines, orchestration, warehousing, distributed data, streaming, quality |
| `tracks/analytics/` | Phase 3: metrics, statistics, EDA, visualization, communication |
| `capstone/` | Phase 4: the end-to-end capstone brief |
| `log/` | Weekly learning log (one file per week, from `log/TEMPLATE.md`) |
| `notes/` | Free-form notes per module |

## Publish with GitHub Pages

1. Merge this branch into `main`.
2. On GitHub go to **Settings → Pages**, set **Source** to *Deploy from a branch*, pick `main` and `/ (root)`.
3. Wait for the build (about a minute). The site appears at `https://pawel-kncck.github.io/data/`.

If you rename the repository, update `baseurl` in `_config.yml` to match.

## Preview locally (optional)

Requires Ruby 3.x and Bundler.

```bash
bundle install
bundle exec jekyll serve
# open http://127.0.0.1:4000/data/
```

## Working the program

- Follow `program/roadmap.md` phase by phase; `program/progress.md` is the checklist.
- Each week, copy `log/TEMPLATE.md` to `log/YYYY-Wnn.md` and fill it in.
- Keep module notes in `notes/`, and project code in a `projects/` folder (or separate repos linked from the module page).
- Edit the modules freely. This is version 0.1; the program should change as I learn what works.
