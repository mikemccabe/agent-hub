# agent-hub

A pared-down sample of how I organize context for Claude Code. Not a
working repo; the content is illustrative.

LLM interactions are ultimately personal: what one person finds useful,
another finds noise. Many context-management tools ship each week; the
mechanism here is just the filesystem.

Read [docs/spec.md](docs/spec.md) for the tour.

## Setup

After cloning, enable the index hook once:

```sh
git config core.hooksPath .githooks
```

It needs `python3` (standard library only).

## What's on display

- **Stub `CLAUDE.md`** — [CLAUDE.md](CLAUDE.md) is a few lines. It
  `@`-includes [docs/spec.md](docs/spec.md) and
  [docs/index.md](docs/index.md), so every session starts from the
  overview and the doc list and follows pointers from there. System
  reference lives in `docs/`, not in `CLAUDE.md`.

- **Durable `docs/`** — long-lived reference. Each doc has an
  `_Updated: YYYY-MM-DD_` line, bumped only for substantive changes.
  Docs describe what the system is; agent behavior stays in
  `CLAUDE.md`.

- **Dated `mds/`** — `YYYY-MM-DD-name.md` working documents for
  planning, investigations, dead ends. Not authoritative: the date
  prefix says they may be stale.

- **Generated indexes** — each doc's frontmatter `summary:` is its
  index entry; [docs/index.md](docs/index.md) and
  [mds/index.md](mds/index.md) are built from those by
  `bin/md-index`, run by a git pre-commit hook. Convention:
  [docs/dated-markdown.md](docs/dated-markdown.md).

- **Multi-repo hub** — one repo where sessions start for work that
  spans several sibling repos, with cross-repo notes kept in its
  `mds/`. See [docs/hub.md](docs/hub.md).
