# projects/

What the subject is actively building or piloting at work. One page per project.

Each project page is an **anchor** — it's the place new raw sources and wiki pages link back to when they touch work the subject is already doing. When a new agentic-SQL tool gets ingested and the subject is mid-build on an agentic SQL workflow, the ingest pass should cross-link the tool's wiki page with the project's anchor page.

## Template

See `CLAUDE.md` — `### projects/ entry` section.

Key fields:
- `status`: active / paused / shipped
- `started`: YYYY-MM-DD
- Lineage section tracing back to the originating `ideas/` entry or raw source
- Current-status notes (not a changelog; just the present state)

## Confidentiality

Per `CLAUDE.md` hard limits: specifics of proprietary data, schemas, or infrastructure stay out of these files. Capture the *shape* of the project, not the internals. If the subject's employer would not want a detail public, it doesn't belong here even if this folder is private — the abstraction discipline keeps the vault portable.
