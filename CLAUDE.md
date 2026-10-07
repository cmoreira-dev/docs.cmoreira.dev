# docs.cmoreira.dev — AI Working Instructions

Public site (MkDocs Material, PT-BR default + EN twin via `.en.md`), published at docs.cmoreira.dev.
This repo is **PUBLIC**: source, history and every branch are visible. Treat every commit as published.

## Public documentation policy

Target model:
1. **Each repo owns its detailed technical documentation** (architecture, diagrams, runbooks, configs,
   endpoints, decisions, backlog, roadmap) in its own private `docs/`, next to the code.
2. **This site is high-level only**: platform overview, patterns, decisions with trade-offs, lessons learned,
   simplified generic diagrams, conventions. Products appear only as short abstract case studies.
   Do not duplicate repo-level detail here.

PUBLIC (keep and improve): overview, architecture patterns, decisions with trade-offs, lessons learned,
generic diagrams, conventions, how-tos written with placeholders.

NOT PUBLIC (belongs in each repo's own docs):
- Detailed technical docs and detailed diagrams of any component or app.
- Product content: roadmap, backlog, brand, pricing, customers, provider setup (e.g. email), API endpoints and
  internals of any app.
- Operational identifiers: IPs/CIDRs, internal hostnames and subdomains, secret paths (SSM/ESO), cloud account /
  tenant / subscription IDs, observability stack/instance names, tokens or where credentials are stored,
  private repo names.
- Open security issues or known vulnerabilities (publish only after fixed, framed as a lesson).

Placeholders: `<app>.example.dev`, `<node-ip>`, `/<scope>/<secret>`, "App A".

**Before committing, list every concrete identifier added in the diff and confirm none is in the NOT PUBLIC
list.** The `public-guard` workflow enforces part of this; it is a backstop, not a substitute.

## Workflow

- Branch + PR; never push to `main` without saying so. Pushes need the user's explicit OK.
- Every page has a PT-BR file (`x.md`) and an EN twin (`x.en.md`) with the same structure. New page: add it to
  `nav:` and its title to `plugins.i18n.languages[en].nav_translations` in `mkdocs.yml`.
- Validate: `./venv/bin/mkdocs build --strict`.
- Design: light theme only, no color-scheme toggle (user decision). The RapportHub design system lives in `docs/assets/css/rh-tokens.css` + `rh-components.css` (copied verbatim from the system; replace both when it changes) and `rh-material.css` (maps them onto MkDocs Material). Rules: header stays light (never `encontro`), no shadows, `acao` for links, coral only as brand marker. Change tokens
  there, not per page.
