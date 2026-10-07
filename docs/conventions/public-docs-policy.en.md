# Public documentation policy

## Model

1. **Each repository owns its detailed technical documentation**: architecture, diagrams, runbooks, configuration,
   endpoints, decisions, backlog and roadmap. It lives in the repository's `docs/`, next to the code.
2. **This site is high-level only:** patterns, decisions with trade-offs, lessons and generic diagrams. Products
   appear as abstract case studies.

## What may and may not appear here

**May:** overview, patterns, decisions with trade-offs, lessons, generic diagrams, how-tos with placeholders.

**May not:** detailed component docs, product content (roadmap, backlog, brand, pricing, customers), operational
identifiers (IPs, internal hostnames, secret paths, account IDs), private repository names and open
vulnerabilities. A lesson is published only after it is fixed.

## Habit before every commit

List every concrete identifier added in the diff and confirm none is on the list above.
Use placeholders: `<app>.example.dev`, `<node-ip>`, `/<scope>/<secret>`, "App A".
