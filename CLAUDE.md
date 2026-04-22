# Career Intel Vault — Project Spec

A Karpathy-style LLM Wiki for **[subject]**, a **[role]** at **[company or context]**. Purpose: scan the AI ecosystem — Substacks, podcasts, articles, GitHub, research — and build a persistent, compounding knowledge base of tools, concepts, and workflows they can implement at work. Oriented toward job-security and promotion: every note earns its place by connecting to something they could actually do in their role.

**Template usage:** search-and-replace `[subject]`, `[role]`, `[company or context]`, `[primary AI tool]`, and `[verification AI tool]` in this file with your own values. Delete this line after.

## Layers

Three layers, per Karpathy's LLM Wiki pattern:

- `raw/` — **immutable sources of truth.** Clipped articles, podcast transcripts, GitHub READMEs, papers. The LLM reads from these; the LLM does NOT modify them. Organized by source type.
- `wiki/` — **LLM-maintained knowledge graph.** Interlinked markdown notes with YAML frontmatter. Nothing here is hand-written — the LLM owns this layer entirely. You read; the LLM writes.
- `CLAUDE.md` — **this file.** The schema. Conventions, workflows, guardrails. Co-evolves as the vault matures.

Career-specific layers (not in Karpathy's base pattern, added because the goal is action not just understanding):

- `projects/` — things [subject] is actively building or piloting at work
- `ideas/` — candidate projects ranked by job-fit (high / med / low)
- `wins/` — shipped outcomes with lineage (source → wiki → idea → project → ship). Promotion-receipts layer.
- `growth/` — recurring themes surfaced from chat archive and from lint passes
- `Chat Archive/` — optional. If populated by a harvester, treat as **private signal — do not republish verbatim.** Mine it for patterns; keep it out of the wiki body. Gitignored in the template.

## General principles

- **Explore the wiki before answering.** Read `wiki/index.md` first. Traverse wikilinks. Link and extend existing notes rather than re-explaining from scratch.
- **Follow existing conventions.** Use whatever frontmatter, tag vocabulary, and wikilink style the existing notes already use. Do not invent new conventions.
- **Grow the vault.** When a new source is ingested or a query produces a useful synthesis, file it back. The wiki must compound.

## Stay inside the signal set

- **Cite only from `raw/` or from wiki pages that themselves cite `raw/`.** No general AI-training-knowledge handwaving. If a concept isn't sourced, say so and offer to ingest a source.
- If something useful exists outside the curated sources, name it as *"not yet in the vault — want me to add [URL] to `raw/`?"* — never silently pull from the open web.
- The `raw/` collection IS the curriculum. Expanding it is a deliberate curatorial act.

## Bandwidth and political context

[Describe [subject]'s time constraints and work environment honestly. Example: "Subject works 6 days a week. Leadership on their team is split between two strategic directions. Their bandwidth is the binding constraint."]

This shapes the vault's filter. A source is worth their attention only if it clears one of two bars:

1. **Supports current work** — saves them effort on something they already have to do.
2. **Too big to skip** — the idea is so load-bearing for their career trajectory that not engaging with it is the bigger risk.

Everything else is noise, even if technically interesting. File it low-signal or skip.

Summaries must be **concise**. [Subject] decides what to act on — the vault does not advocate, it reports. Lead with the verdict; let them read deeper only if they choose.

## The Subject Angle — the filter that makes this career-compounding

Every wiki page of type `tool`, `concept`, or `workflow` MUST open with a **one-line verdict** (TL;DR) and end with a **Subject Angle** block:

- `priority:` high | med | low — fit with their role
- `time_cost:` net-saves-time | zero-cost | small-lift | big-lift — what adopting this actually costs in hours
- `strengthens_current_work:` yes | adjacent | no — does this make existing workload easier or higher-quality?
- `too_big_to_skip:` yes | no — is this so career-load-bearing that skipping is the bigger risk?
- `how_they_could_use_this:` 1–3 sentences, concrete
- `connects_to:` `[[wikilinks]]` to `projects/` or `ideas/` entries if any exist

A page earns `priority: high` only if it is `strengthens_current_work: yes` OR `too_big_to_skip: yes`. Everything else is med or low.

If an ingested source produces nothing with priority high or med, file it anyway but flag it in `log.md` as low-signal. Source quality gets pruned over time based on this signal.

## Be thorough on external scanning

We are in the middle of an AI race. New GitHub projects, Substacks, and papers drop daily that could materially help [subject]. When scanning a new source, be **incredibly thorough** — don't skim. The job of the vault is to catch the one idea in ten that actually clears the bandwidth filter. Low hit rate is expected; shallow scanning is not.

## Citation format (dual-link)

Every answer ends with a **Sources** block containing at least two different *kinds* of source (a `raw/` file + a wiki page; or a wiki page + an external URL already noted in a wiki page). Use dual-link format so citations work in both chat and Obsidian:

- In chat: file links (clickable)
- Alongside: `[[wikilink]]` form in parentheses (Obsidian resolution)
- Use shortest unique wikilink path: `[[cursor-composer]]`, not `[[wiki/tools/cursor-composer]]`

**Verify before citing.** Confirm the file exists. Never invent paths.

## Operations (Karpathy: ingest / query / lint)

### Ingest

[Subject] or a collaborator drops a new source into `raw/<category>/`. Process:

1. Read the source in full.
2. Discuss key takeaways in chat (1–2 paragraphs).
3. Write a `source-summary` page in `wiki/` linking to the raw file.
4. Update or create `concept` / `tool` / `workflow` / `person` / `company` pages touched by this source. A single source can touch 10–15 wiki pages.
5. Update `wiki/index.md` with any new pages.
6. Append to `wiki/log.md` in format `## [YYYY-MM-DD] ingest | <Source Title>`, followed by 1–3 lines summarizing takeaways and listing pages touched.
7. Explicitly flag Subject Angle priority on any new tool/concept/workflow page.

Prefer one source at a time with [subject] in the loop.

### Query

1. Read `wiki/index.md`.
2. Identify relevant pages. Traverse wikilinks to pull in context.
3. Synthesize a citation-backed answer.
4. If the answer produced a useful new synthesis (comparison, analysis, connection), **offer to file it back** as a new wiki page.
5. If the query reveals a missing concept (no page exists), offer to ingest a source that covers it.

### Lint

Invoked manually ("lint the vault"). Report:

- Contradictions between pages
- Stale claims superseded by newer sources
- Orphan pages (no inbound links)
- Concepts mentioned but not given their own page
- Missing cross-references
- Data gaps that could be filled by web search (offer specific queries)
- Recurring themes from `wiki/log.md` that deserve a `growth/` note

## Chat archive as signal source (optional)

If a chat-archive harvester populates `Chat Archive/`, mine it during ingest and lint for:

- Topics [subject] has asked about repeatedly → candidate `growth/` note + dedicated wiki page
- Tools they've mentioned trying or wanting to try → candidate `wiki/` tool page + `ideas/` entry
- Work contexts they've described → enrich the Subject Angle filter

Do NOT copy chat-archive contents into wiki pages. Treat as private signal that informs what to investigate in external sources.

**Scoping note — multi-model workflows:** If [subject] uses one model (e.g., [primary AI tool]) for day-to-day work and another (e.g., [verification AI tool]) for complex or verification tasks, the archive of the complex-task model is pre-filtered to high-stakes work — signal density is high but it under-represents routine workload. When evaluating new tools, ask "does this beat [primary AI tool] on the complex-task slice?", not "does this beat nothing."

## Page templates

### `wiki/` concept / tool / workflow

```yaml
---
type: concept | tool | workflow
aliases: []
tags: []
sources: [[source-id-1]], [[source-id-2]]
---

> **Verdict:** one-sentence TL;DR — what this is and whether [subject] should care.

## What it is

## Why it matters

## Related
[[other-concept]], [[other-tool]]

## Subject angle
priority: high | med | low
time_cost: net-saves-time | zero-cost | small-lift | big-lift
strengthens_current_work: yes | adjacent | no
too_big_to_skip: yes | no
how_they_could_use_this: ...
connects_to: [[...]]
```

### `wiki/` source-summary

```yaml
---
type: source-summary
source_file: raw/<path>
source_kind: substack | podcast | article | github | paper
date_published: YYYY-MM-DD
date_ingested: YYYY-MM-DD
author: [[person-page]]
---

## Key takeaways

## Pages touched
- [[page-a]]
- [[page-b]]
```

### `ideas/` entry

```yaml
---
type: idea
status: candidate | piloting | shelved
priority: high | med | low
origin: [[source-or-wiki-page]]
---

## The idea

## Why it fits [subject]'s role

## Smallest next step

## Signal to look for
```

### `projects/` entry

```yaml
---
type: project
status: active | paused | shipped
started: YYYY-MM-DD
---

## What they're building

## Lineage
origin: [[idea-or-source]]

## Current status
```

### `wins/` entry

```yaml
---
type: win
shipped: YYYY-MM-DD
project: [[project-page]]
---

## What shipped

## Lineage (receipts)
source: [[...]] → wiki: [[...]] → idea: [[...]] → project: [[...]] → shipped YYYY-MM-DD

## Impact
(metrics, review-quotable outcomes)
```

## Style rules

- `kebab-case` for filenames.
- YAML frontmatter on every wiki page.
- One idea per page. Split if a page grows past ~500 words unless it's intentionally a long synthesis.
- Note intros describe *what*, not *how*. Implementation lives in raw sources.
- No emojis in page bodies.

## Hard limits

- **Never act on [subject]'s workplace systems.** The vault informs; they execute. No auto-emails, no PRs, no Slack posts to work channels.
- **Never export or share chat-archive contents outside this vault.**
- **Never put confidential work material into `wiki/` body pages.** If a raw source contains internal/proprietary info, keep it in `raw/internal/` and reference only at the abstraction level needed for a tool/concept page.

## Environment

The vault folder should be the selected workspace when operating on this vault — keeps file paths stable for the LLM.
