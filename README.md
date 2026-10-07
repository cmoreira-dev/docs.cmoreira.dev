# docs.cmoreira.dev

Public, high-level notes on a homelab platform: patterns, decisions with trade-offs, lessons learned and abstract
case studies. Detailed technical docs live in each (private) repository's `docs/`.

See `docs/conventions/public-docs-policy.md` and `CLAUDE.md` for what may be published here.

```bash
python3 -m venv venv && ./venv/bin/pip install -r requirements.txt
./venv/bin/mkdocs serve          # live preview
./venv/bin/mkdocs build --strict
```

Design: RapportHub design system (tokens + components in `docs/assets/css/`), Plus Jakarta Sans + Source Serif 4 self-hosted (OFL licences in `docs/assets/fonts/`).
