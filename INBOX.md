# INBOX — free-form context drops

Paste anything about the subject here — context from conversations with them, mood/bandwidth updates, new projects, something they said they're reading, a tool they're evaluating, a political context from their team, a decision point they're weighing. Anything.

On each weekly digest run, the LLM will:

1. Read new entries here
2. Route each entry against existing anchor pages in `projects/`, `growth/`, and `wiki/` — or create new pages if needed
3. Mark processed entries with a `[processed YYYY-MM-DD]` tag + a one-line note of what was done
4. Preserve original text as-is (append-only; don't delete unless you want to)
5. Use the new context to re-tune the week's digest

## Format

Add entries with a date header. Dump however it came to you — voice-to-text, copy-paste, fragments, whatever. The LLM will parse it.

```
## [YYYY-MM-DD] short topic
free-form text here
```

## Optional tags (the LLM will read these if present, otherwise infer)

- `#urgent` — address in this week's digest, not next
- `#private` — don't surface to the subject's digest, just shape filter
- `#career` — promo / recruiting / political context
- `#project:<name>` — routes to a specific project page
- `#skip` — noted but not actionable, archive

---

## Entries

*(no entries yet — paste below this line)*
