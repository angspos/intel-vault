# Career Intel Vault

A personal knowledge system for absorbing the AI ecosystem's signal without burning your weekends. Built on Andrej Karpathy's LLM Wiki pattern, extended with a bandwidth-aware filter and a weekly digest automation loop.

Use this template if you are an individual contributor who wants to stay current on AI tooling, research, and adjacent engineering craft, all while increasing productivity — but a firehose of newsletters, GitHub trending lists, and arXiv isn't how you want to spend your free time.

This framework works with any LLM you can have a conversation with. It pulls from external sources (articles, papers, GitHub) and — optionally — your own chat history, filters against your actual work and career trajectory, and produces a weekly digest that surfaces recurring growth themes, compares your workflows against cutting-edge tooling, and names knowledge gaps with concrete bridges to close them. The weekly-digest automation assumes an agentic setup (scheduled tasks + tool use) — if you only have a chatbot, run the digest manually each week.

## What it is

The vault has three layers, per Karpathy's LLM Wiki pattern:

- **`raw/`** — immutable external sources. Clipped articles, papers, podcast transcripts, GitHub READMEs. The LLM reads from these; the LLM does not modify them.
- **`wiki/`** — LLM-maintained knowledge graph. Interlinked markdown notes with YAML frontmatter. The LLM owns this layer entirely.
- **`CLAUDE.md`** — the behavioral contract. Conventions, operations, guardrails. Co-evolves with the vault.

Four career-specific layers on top (not in Karpathy's base pattern — added because the goal is action, not just understanding):

- **`projects/`** — things you are actively building or piloting at work
- **`ideas/`** — candidate projects, ranked by role-fit
- **`growth/`** — recurring themes the vault has surfaced, with bridges
- **`wins/`** — shipped outcomes with lineage (source → wiki → idea → project → ship). The promotion-receipts layer.

## Design decisions worth calling out

The template enforces four decisions that make the vault compound rather than accumulate:

**1. Verdict-first.** Every wiki page leads with a one-sentence verdict. The vault reports; you decide. No advocacy, no hedged "you might consider..." The filter is strict enough that items that make it in deserve a direct claim about whether they matter.

**2. Bandwidth-aware filter.** Every `concept`, `tool`, or `workflow` page carries four Subject-Angle fields:
- `priority`: high / med / low
- `time_cost`: net-saves-time / zero-cost / small-lift / big-lift
- `strengthens_current_work`: yes / adjacent / no
- `too_big_to_skip`: yes / no

A page earns `priority: high` only if `strengthens_current_work: yes` OR `too_big_to_skip: yes`. Everything else is med, low, or filed-but-flagged. This is the core anti-noise mechanism.

**3. Citation discipline.** Claims are sourced from `raw/` or from wiki pages that cite `raw/`. No open-web handwaving. If the LLM tries to answer something unsourced, it flags the gap and offers to ingest a source. The `raw/` collection IS the curriculum — expanding it is a deliberate curatorial act.

**4. Automation loop.** A weekly scheduled task reads a free-form `INBOX.md`, any new external sources, and any new archive signal. If qualifying items clear the bandwidth filter, it produces a concise digest (markdown + Word doc). If nothing clears, it skips the week and logs why. Low-signal weeks produce no noise.

## How it works end-to-end

```
 Context sources                Processing                     Output
 ───────────────                ──────────                     ──────
 RSS / GitHub / arXiv   ──┐
                          │
 Chat archive (private)  ──┼──►  Weekly digest task  ──►  growth/weekly-YYYY-MM-DD.md
                          │     (skip-if-low-signal)         +
 INBOX.md (freeform)    ──┘                               Weekly Digest.docx
                                                            (for sharing)
```

## Getting started

1. Fork this repo and rename it however you want.
2. Open `CLAUDE.md` and replace the placeholder persona with yours (or whoever the vault is for). The `[subject]`, `[role]`, `[tools]`, and `[bandwidth context]` placeholders are the minimum to fill in.
3. Populate `raw/` with 3–5 sources you have been meaning to read. Bias toward quality over volume for the first pass.
4. Open the repo in a Claude conversation and say: "ingest `raw/articles/[filename]`". The vault will walk through the ingest pattern.
5. Optional: set up the weekly digest automation. See `docs/automation.md`.

## What makes this different from other knowledge-vault templates

Most personal knowledge systems either (a) accumulate without filtering, turning into a graveyard, or (b) filter so aggressively they stop compounding. The bandwidth-filter + verdict-first combination is designed to do both: filter hard at the input (so only qualifying items earn full ingestion) *and* compound at the output (each ingested item potentially touches 10–15 wiki pages, because wikilinks let the graph grow fast).

The `too_big_to_skip` field is also load-bearing in a way other templates miss. Most career-productivity systems only surface "what helps you today." This one also surfaces "what is too load-bearing for your trajectory to ignore, even if it costs you." Those are different questions and both matter.

## Credits

- Andrej Karpathy's [LLM Wiki gist](https://gist.github.com/karpathy) (the base pattern)
- ML-Course-Vault ([link to repo](https://github.com/angspos/ai-augmented-learning)) — an earlier instantiation of the pattern, applied to coursework

## License

MIT — see [LICENSE](LICENSE).

## Status

Template is stable. The example persona + example weekly-digest in `examples/` illustrate what the vault produces. Automation scripts are in `docs/automation.md` — wire them up to whatever scheduler you prefer.

This repo is a sanitized template extracted from a working personal instance. The working instance stays private; this template is what I'd fork if I were setting it up from scratch.
