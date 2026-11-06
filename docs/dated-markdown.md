---
summary: >-
  Conventions for durable docs/ and dated mds/ -- frontmatter summaries,
  the generated indexes, _Updated lines, companion directories,
  supersession.
---

# Markdown Documents

_Updated: 2026-11-06_

Two flavors:

- **`docs/`** — long-lived reference. Describes what the system is.
- **`mds/`** — dated working documents. Planning, investigation,
  dead ends at a point in time.

## Frontmatter and the generated indexes

Every doc in both directories starts with a YAML frontmatter block. The
one required key is `summary:`, the doc's index entry:

```markdown
---
summary: >-
  Why checkout got slow in early November: a smaller API connection
  pool. Fixed by restoring the pool size.
---

# 2026-11-06 Slow checkout page
```

`docs/index.md` and `mds/index.md` are generated from those summaries
by `bin/md-index` and committed. The git pre-commit hook in
`.githooks/` regenerates them from the staged docs and stages the
result, so a commit that adds a doc or changes a summary carries the
index update with it. The hook is enabled per clone with
`git config core.hooksPath .githooks`; without it, run `bin/md-index`
before committing. `bin/md-index --check` exits non-zero when an index
is stale.

Summaries are pointers, not abstracts: topic, key finding or outcome,
and any status (superseded, open, corrected). Details, numbers, and
follow-ups belong in the doc. A reader scans the index to decide
*which* doc to open; the doc answers *what's in it*. When a doc gets a
later follow-up, revise the summary's outcome rather than appending a
second story.

Use a block scalar (`>-`) for any summary longer than a line or
containing `: `, which plain YAML values cannot hold.

## docs/

Each long-lived doc carries `_Updated: YYYY-MM-DD_` right after the H1
(blank line on each side). Bump for substantive changes — new sections,
factual corrections, structural rewrites. Don't bump for typo fixes,
link tweaks, or formatting-only changes. ISO format.

Content is agent-agnostic: describe the system, not how agents should
behave. Agent behavior belongs in `CLAUDE.md`.

## mds/

Filenames are date-prefixed: `YYYY-MM-DD-name.md`. Only date-prefixed
files are indexed.

### Philosophy

These are **not authoritative**. The date prefix signals documents may go
stale — they capture planning, investigations, dead ends, and
implementations at a point in time. Verify against code and git history
before trusting any document.

### Structure

```
mds/
  index.md                       # generated
  2026-05-27-feature-plan.md
  2026-05-28-api-design.md
  2026-05-29-chart/              # companion asset bundle (same date prefix)
```

A dated doc may have a sibling directory with the **same date prefix**
holding companion assets (served HTML, structured data, scraped sources,
helper scripts). Date the directory like the doc so it stays grouped
chronologically and obviously paired.

### Supersession

When a newer dated doc replaces an older one, leave the old file in place
and add a brief preamble at the top pointing to the replacement — one to
two lines, italicized, immediately after the H1 — and mark the old doc's
summary as superseded:

```markdown
# 2026-04-12 Feature Plan

_Superseded 2026-05-20 by [2026-05-20-feature-plan-v2.md](2026-05-20-feature-plan-v2.md).
Kept for the original requirements analysis._
```

Do not delete or rewrite the old doc — it remains the historical record
for that point in time. Only the preamble and summary change.
