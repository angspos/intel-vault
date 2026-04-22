# Sidharth Intel Vault

A persistent, LLM-maintained knowledge base for Sidharth — a Senior Data Scientist — oriented around making him indispensable at his job.

The vault ingests signal from the AI ecosystem (Substacks, podcasts, articles, GitHub, research) and compounds it into a graph of tools, concepts, and workflows, each tagged with "how he could use this at work." Over time, that graph feeds a pipeline: **raw source → wiki page → idea → project → shipped win**. The `wins/` folder is the receipts layer — lineage-tracked outcomes for performance reviews and promotion conversations.

Modeled on Andrej Karpathy's [LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) with career-specific additions. `CLAUDE.md` is the behavioral contract — read it first, it governs everything else.

## The layers

- `raw/` — immutable sources. Claude reads, never modifies.
- `wiki/` — Claude-maintained knowledge graph. Markdown + wikilinks. Humans read; Claude writes.
- `CLAUDE.md` — the schema. Conventions, workflows, guardrails.
- `projects/` `ideas/` `wins/` `growth/` — career-specific layers. Where intel turns into action.
- `Claude Chat Archive/` — private signal source, auto-populated weekly by the `claude-chat-export-harvester` scheduled task.

## The three operations

- **Ingest** — drop a source into `raw/<category>/`, ask Claude to process. It writes a summary, updates the graph, logs the event.
- **Query** — ask a question against the vault. Claude reads `wiki/index.md`, traverses links, answers with citations. Useful syntheses get filed back.
- **Lint** — periodic health check. Claude surfaces contradictions, orphan pages, missing concepts, recurring themes to promote into `growth/`.

## Getting started

1. Open the vault in Obsidian (point Obsidian at this folder).
2. Read `CLAUDE.md`.
3. Clip your first article — drop it in `raw/articles/`.
4. In Cowork, ask: *"Ingest the new article in raw/articles/."*
5. Watch Claude write the first wiki pages, update `index.md`, and log the event.

The vault gets smarter as you feed it. The goal isn't volume — it's *coverage* against Sidharth's job plus *connection density* between notes.
