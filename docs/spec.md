---
summary: Repo overview -- what this hub is and its layout. Start here.
---

# agent-hub

_Updated: 2026-11-06_

A sample hub repo for working with a coding agent across several
sibling repos. The docs describe conventions; `mds/` holds an
illustrative sample entry.

## Layout

| Path | Contents |
|------|----------|
| `CLAUDE.md` | Agent instructions; `@`-includes this file and `docs/index.md` |
| `docs/` | Durable reference, listed in [index.md](index.md) |
| `mds/` | Dated working documents, listed in [../mds/index.md](../mds/index.md) |
| `bin/md-index` | Generates both indexes from each doc's `summary:` frontmatter |
| `.githooks/pre-commit` | Runs `bin/md-index` and stages the indexes |

Both indexes are generated and committed, so they read correctly on the
web and in a fresh clone. The hook keeps them current; it is enabled
per clone (see the README).
