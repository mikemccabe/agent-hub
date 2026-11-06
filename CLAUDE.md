# agent-hub

A hub repo: where agent sessions start, with their context kept as
plain files -- durable `docs/` and dated `mds/`.

See @docs/spec.md for overview and @docs/index.md for the docs.
Working documents are listed in `mds/index.md`; search it rather than
reading it whole.

## Frontmatter and indexes

Every doc in `docs/` and `mds/` starts with a YAML frontmatter block
whose `summary:` is its index entry. Write or revise the summary when
adding or substantively changing a doc. Never edit `docs/index.md` or
`mds/index.md` by hand: the pre-commit hook regenerates them, and
`bin/md-index` does the same when the hook is not enabled.

## Suggesting an md

When a chat reaches a meaningful conclusion -- a finding, a decision, a
dead end worth not repeating -- suggest "make an md" in one line. Don't
create or keep editing one unprompted; the user decides.

## Writing in docs/

Before adding a number, a version, a list of things, or a status line
to a `docs/` page, apply "Keeping churn out of docs/" in
[docs/dated-markdown.md](docs/dated-markdown.md): the query rather than
the answer, scale rather than a count, status in an md.

## Doc timestamps

Long-lived docs under `docs/` carry an `_Updated: YYYY-MM-DD_` line
right after the H1 (blank line on each side). Bump it for substantive
revisions -- new sections, factual corrections, structural rewrites --
not for typo fixes, link tweaks, or formatting. Working documents under
`mds/` encode their date in the filename instead. Full convention in
[docs/dated-markdown.md](docs/dated-markdown.md).
