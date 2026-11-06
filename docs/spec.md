# agent-hub

_Updated: 2026-11-06_

A sample hub repo for working with a coding agent across several
sibling repos. The docs describe conventions; `mds/` holds an
illustrative sample entry.

## Layout

| Path | Contents |
|------|----------|
| `CLAUDE.md` | Agent instructions; `@`-includes this file |
| `docs/` | Durable reference, indexed here |
| `mds/` | Dated working documents, indexed by `mds/index.md` |

## Docs

- [hub.md](hub.md) — the multi-repo hub pattern and the
  `additionalDirectories` setting that makes cross-repo reads work
- [dated-markdown.md](dated-markdown.md) — conventions for durable
  `docs/` and dated `mds/`
