---
summary: Repo overview -- what this hub is for and its layout. Start here.
updated: 2026-11-06
---

# agent-hub

A hub repo for working with a coding agent across several repos,
projects or subjects: sessions start here, and their context lives in
`docs/` and `mds/` as plain files under git.

## Layout

| Path | Contents |
|------|----------|
| `CLAUDE.md` | Agent instructions; `@`-includes this file and `docs/index.md` |
| `docs/` | Durable reference, listed in [index.md](index.md) |
| `mds/` | Dated working documents, listed in [../mds/index.md](../mds/index.md) |
| `bin/md-index` | Generates both indexes from each doc's `summary:` frontmatter |
| `.claude/skills/md/` | The `/md` skill: create a dated md per [dated-markdown.md](dated-markdown.md) and commit it |
| `.githooks/` | `pre-commit` runs `bin/md-index` and stages the indexes; `post-commit` resyncs them after a pathspec commit |

Both indexes are generated and committed, so they read correctly on the
web and in a fresh clone. The hook keeps them current; it is enabled
per clone (see the README).
