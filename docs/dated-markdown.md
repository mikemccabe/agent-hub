---
summary: >-
  Conventions for durable docs/ and dated mds/ -- layered detail, keeping
  churn out of docs/, demoting a page, frontmatter summaries and the
  generated indexes, checking for prior mds, naming plan elements,
  citing mds, companion directories, supersession.
---

# Markdown Documents

_Updated: 2026-11-06_

Two flavors:

- **`docs/`** — long-lived reference. Describes what the system is.
- **`mds/`** — dated working documents. Planning, investigation,
  dead ends at a point in time.

## docs/

Each long-lived doc carries `_Updated: YYYY-MM-DD_` right after the H1
(blank line on each side). Bump for substantive changes — new sections,
factual corrections, structural rewrites. Don't bump for typo fixes,
link tweaks, or formatting-only changes. ISO format.

Content is agent-agnostic: describe the system, not how agents should
behave. Agent behavior belongs in `CLAUDE.md`.

### Layered detail

A fact lives at the innermost layer that serves its reader, once:

1. **The tool or config itself.** Best is making the doc unnecessary:
   fix the footgun (an option, a guard, a better error), let `--help`
   own the recipes, and put a caveat that guards an edit site in a
   comment at that site.
2. **The `docs/` page.** What it is, how to invoke it, and pointers
   down. It does not restate the layers above or below.
3. **The dated md.** Mechanism, evidence, history, dead ends.

When detail cannot be deferred safely -- an innocent-looking edit would
break something silently -- the page carries a one-line warning and a
pointer, not the mechanism.

Work in flight on a page's subject shows on the page as one line
pointing at its md, removed when the work ends. The page changes only
when the system it describes changes; the work's status and history
stay in the md.

### Keeping churn out of docs/

A precise fact whose half-life is shorter than the page's revision
cadence is a churn center: it reads stale on the next visit, and the
next review spends effort re-deriving a figure nobody acts on. The page
carries the structure; the number lives where it is generated.

- **The query, not the answer.** Where a reader can run a command, the
  page gives the command and at most one dated sample of its output.
- **Scale, not census.** "Thousands of hosts" stays true for years. A
  precise count appears only when the count is the point, and then
  dated.
- **A rule, not a value, for anything that tracks usage.** Growth,
  ratios, shares. When a value is needed: one dated range in one place,
  every other mention relative to it.
- **Config values appear once, with their file named.** Other pages
  point at that page.
- **Names, not line numbers.** Citations into code name the function,
  variable or setting; line numbers move.
- **Versions: a floor or a pin is kept; what's running today is a
  query.**
- **Status lines go to an md.** "Still open", "not yet", "currently",
  "as of" go stale silently. The page keeps at most a one-line pointer.
- **One figure, one home.** A number stated on two pages drifts on one
  of them; the second page points at the first.
- **A measurement that is the deliverable is an md**; the page cites
  it.
- **Provenance dates stay.** "Verified 2026-07-15" tells the reader how
  old the check is; refresh it only when the fact is re-checked.
- **Drift gets this treatment, not a new number.** A fresher figure
  written in reads stale again by the next visit.

A page whose table is the record (an inventory, a key list) says so in
one line and is exempt.

### Demoting a page to mds/

`docs/index.md` is loaded into every session, so each entry costs
startup context indefinitely; `mds/index.md` is read only on demand. A
page earns its place while a session might need it unprompted. When
that stops -- the service is retired, the tool unused -- `git mv` it to
`mds/YYYY-MM-DD-<slug>.md` dated the day of the move, note the move and
its reason in its summary, and re-point any links to it in the same
commit.

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

Optional keys: `status: superseded` and `superseded-by: <file>` (see
[Supersession](#supersession)). Derivable facts are not fields: no
`title:` (the H1 has it) and no `date:` (the filename has it).

Use a block scalar (`>-`) for any summary longer than a line or
containing `: `, which plain YAML values cannot hold.

`docs/index.md` and `mds/index.md` are generated from the summaries by
`bin/md-index` and committed. The git pre-commit hook in `.githooks/`
regenerates them from the staged docs and stages the result, so a
commit that adds a doc or changes a summary carries the index update
with it. The hook is enabled per clone with
`git config core.hooksPath .githooks`; without it, run `bin/md-index`
before committing. `bin/md-index --check` exits non-zero when an index
is stale.

### Keep the summary a pointer

A summary gives the topic, the key finding or outcome, and any status,
in one paragraph. There is no word budget: the index is searched by
keyword and scanned by recency, never read whole, so a summary rich in
the terms a later search would use is worth more than a terse one. What
it must not become is a second body: method, measurements, file paths
and follow-up lists belong in the doc.

**The summary does not grow with the doc.** On every edit, rewrite it
from the doc's current bottom line: new conclusions displace
intermediate ones rather than joining them. A summary that holds
timestamps, "Addendum:", or phase-by-phase developments has become a
chronology; that belongs in the body.

## mds/

Filenames are date-prefixed: `YYYY-MM-DD-name.md`. Only date-prefixed
files are indexed.

### Philosophy

These are **not authoritative**. The date prefix signals documents may go
stale — they capture planning, investigations, dead ends, and
implementations at a point in time. Verify against code and git history
before trusting any document.

### Check for priors first

Before creating an md, scan `mds/index.md` and the filenames for prior
docs on the topic -- a quick scan, not research. Then:

- **A prior doc already is this deliverable** (the same finding, seen
  again): don't create one. Revise the prior's summary, or supersede it.
- **Related but distinct:** create it, and cite the prior where it is
  load-bearing. No exhaustive "Related" lists.
- **New development on an old topic:** prefer one md per topic. When
  the new work revises or extends a prior md -- the same question, a
  better answer -- update the prior and rewrite its summary. Start a
  new md that cites the old one when the new work asks a different
  question, or when the prior is worth keeping as the record of its
  time.

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

### Naming plan elements

When a doc defines an enumerated plan -- phases, options, tiers -- give
each element a short kebab-case name where it is defined:
`Phase 1 (pool-restore)`, `Option A (read-repair)`. Later references
anywhere (other docs, commits, chat) carry both forms. Ordinals shift
when a plan is revised; names stay pinned.

A name says what the element does, in the definition's own words: a
component or a bare verb (`api`, `cutover`) says which thing, not what
about it. Name only elements likely to be cited from outside the doc --
decision points, competing options. Steps read in order inside their
own doc keep bare ordinals. Names are minted once, at the definition;
a doc citing another doc's plan uses its names.

### Citing mds

Link with the filename as the target and a short natural mention --
usually the slug -- as the text:
`[slow-checkout](2026-11-06-slow-checkout.md)`. Never repeat the full
filename as the text; the target carries the stable identity and keeps
citations greppable.

### Supersession

Supersede when a new doc replaces an old one's conclusions; citing or
building on a prior is not supersession.

Leave the old file in place. In its frontmatter set
`status: superseded` and, when there is one successor,
`superseded-by: <filename>`; the index marks the entry. For human
readers, add a brief italic preamble right after the H1:

```markdown
# 2026-04-12 Feature Plan

_Superseded 2026-05-20 by [feature-plan-v2](2026-05-20-feature-plan-v2.md).
Kept for the original requirements analysis._
```

Do not delete or rewrite the old doc — it remains the historical record
for that point in time. Only the frontmatter and preamble change.
