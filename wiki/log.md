# Log

Chronological, append-only record of wiki events. Format per Karpathy:

```
## [YYYY-MM-DD] ingest | Source Title
1-3 line summary of takeaways.
Pages touched: [[page-a]], [[page-b]]
Subject angle: high | med | low
```

Use consistent `## [` prefix so `grep "^## \[" log.md | tail -10` works.

Event types: `ingest`, `query-filed` (when a query synthesis got filed as a new page), `lint`, `promotion` (when something moved from `ideas/` to `projects/` or from `projects/` to `wins/`), `digest-delivered`, `digest-skipped`.

---

*(no entries yet)*
