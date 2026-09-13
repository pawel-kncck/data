---
title: "Phase 0: Setup"
nav_order: 3
---

# Phase 0 · Setup
{: .no_toc }

**Time budget:** 1 week (8 h) · **Prereqs:** none

1. TOC
{:toc}

## Why this matters

Every later module assumes I can start a database, run Python, and commit work without thinking
about it. Environment problems in week six are motivation killers; this week absorbs them up front.
It also sets up the habits (log, notes, weekly rhythm) the program depends on.

## Learning outcomes

By the end of this week I can:

- start and stop PostgreSQL and connect to it from a terminal and from Python;
- run a Python project with `uv` and an isolated environment;
- query a CSV or Parquet file with DuckDB in under a minute;
- keep this site, my notes and my project code in git and see them published.

## Study

| Resource | What to do | Est. |
| --- | --- | --- |
| [Docker Compose overview](https://docs.docker.com/compose/) | Read the "how Compose works" page only. | 0.5 h |
| [uv docs: projects](https://docs.astral.sh/uv/guides/projects/) | Read the projects guide. | 0.5 h |
| [DuckDB: Python API](https://duckdb.org/docs/api/python/overview) | Skim; run the examples. | 0.5 h |
| [psql cheat sheet in the Postgres manual](https://www.postgresql.org/docs/current/app-psql.html) | Learn `\l \c \dt \d \x \timing`. | 0.5 h |

## Practice

1. Install: Docker, `uv`, Python 3.12+, VS Code (with Python and SQL extensions), `psql` client, `git`.
2. Create `projects/` in this repo (or a separate repo) with a `docker-compose.yml` that starts PostgreSQL 16 with a named volume. Connect with `psql`. Create a database called `learning`.
3. In a `uv` project, install `duckdb`, `polars`, `psycopg[binary]`, `jupyterlab`. Read a CSV with DuckDB, count its rows, write it back as Parquet.
4. From Python, connect to Postgres, create a table, insert three rows, read them back.
5. Publish this site with GitHub Pages (instructions in the repo README). Confirm it renders.
6. Create the first [learning log](../log/index.md) entry from the template.

## Build

A `projects/README.md` that documents, in ten lines or fewer, how to bring the environment up
from a clean machine. Test it by deleting the containers and volumes and following the README.

## Check yourself

- What does `docker compose down -v` do that `docker compose down` does not?
- Where does `uv` put the virtual environment, and how do I run a script inside it?
- How do I see which database and user I am connected to in `psql`?
- Why does DuckDB not need a server process?

## Done when

- [ ] Postgres runs via Compose and survives a restart with its data intact.
- [ ] A `uv` project exists with the listed packages; `uv run python -c "import duckdb, polars"` works.
- [ ] The site is live on GitHub Pages.
- [ ] `projects/README.md` reproduces the environment from scratch.
- [ ] First log entry written.

## My notes

_Link to `notes/m00-setup.md` once written._
