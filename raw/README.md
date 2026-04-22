# raw/ — immutable sources of truth

This is where external sources live in full: clipped articles, podcast transcripts, GitHub READMEs, papers, newsletter issues. The LLM reads from here but does not modify these files. If a source needs updating, you add a new version as a new file rather than editing the old one.

## Subfolder conventions

- `substack/` — newsletter / blog posts (Simon Willison, Latent Space, Ethan Mollick, Eugene Yan, etc.)
- `podcasts/` — podcast transcripts (Latent Space, Dwarkesh, No Priors, etc.)
- `articles/` — longer-form articles not from a regular newsletter
- `github/` — cloned READMEs and key docs from trending repos
- `research/` — arXiv papers, other academic sources
- `internal/` — any sensitive/proprietary material the subject shares with the vault. **Gitignored by convention.** Reference at abstraction level only in `wiki/` body pages.
- `assets/` — images, diagrams, figures extracted from sources

## Filename convention

`YYYY-MM-DD-short-title.md` for dated sources. `kebab-case` for everything.

## What goes in a raw file

Whatever format the source arrived in. A scraped article stays as markdown with the original structure. A GitHub README stays as its README. A podcast transcript stays as a transcript. The LLM's job is to read the raw and produce the wiki-layer synthesis — don't pre-digest inside `raw/`.

## What does NOT go in raw/

- Your own notes on a source — those go in `wiki/` as the source-summary page
- Synthesized comparisons across sources — those go in `wiki/` as concept pages
- Chat-archive contents — those have their own separate folder, gitignored
