# Markdown Documents

_Updated: 2026-11-06_

Two flavors:

- **`docs/`** — long-lived reference. Describes what the system is.
  Indexed by `docs/spec.md`.
- **`mds/`** — dated working documents. Planning, investigation,
  dead ends at a point in time. Indexed by `mds/index.md`.

## docs/

Each long-lived doc carries `_Updated: YYYY-MM-DD_` as the second line of
the file (right after the H1, blank line on each side). Bump for
substantive changes — new sections, factual corrections, structural
rewrites. Don't bump for typo fixes, link tweaks, or formatting-only
changes. ISO format.

Content is agent-agnostic: describe the system, not how agents should
behave. Agent behavior belongs in `CLAUDE.md`.

## mds/

Filenames are date-prefixed: `YYYY-MM-DD-name.md`

### Philosophy

These are **not authoritative**. The date prefix signals documents may go
stale — they capture planning, investigations, dead ends, and
implementations at a point in time. Verify against code and git history
before trusting any document.

### Structure

```
mds/
  index.md                       # Document index with descriptions
  2026-05-27-feature-plan.md
  2026-05-28-api-design.md
  2026-05-29-chart/              # companion asset bundle (same date prefix)
```

A dated doc may have a sibling directory with the **same date prefix**
holding companion assets (served HTML, structured data, scraped sources,
helper scripts). Date the directory like the doc so it stays grouped
chronologically and obviously paired.

### Index

Keep `mds/index.md` updated with brief descriptions, grouped by month.

Index entries are pointers, not summaries. Aim for **1-4 lines** per
entry: topic, key finding or outcome, and any status flag from the doc
itself (`**superseded**`, `**temporary**`, `**corrected**`). Details,
numbers, and follow-ups belong in the doc. A reader scans the index to
decide *which* doc to open; the doc answers *what's in it*.

### Supersession

When a newer dated doc replaces an older one, leave the old file in place
and add a brief preamble at the top pointing to the replacement — one to
two lines, italicized, immediately after the H1:

```markdown
# 2026-04-12 Feature Plan

_Superseded 2026-05-20 by [2026-05-20-feature-plan-v2.md](2026-05-20-feature-plan-v2.md).
Kept for the original requirements analysis._
```

Do not delete or rewrite the old doc — it remains the historical record
for that point in time. Only the preamble changes.
