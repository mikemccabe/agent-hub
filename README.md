# agent-hub

A pared-down sample of how I organize context for Claude Code. Not a
working repo; the content is illustrative.

LLM interactions are ultimately personal: what one person finds useful,
another finds noise. Many context-management tools ship each week; the
mechanism here is just the filesystem.

Read [docs/spec.md](docs/spec.md) for the tour.

## What's on display

- **Stub `CLAUDE.md`** — [CLAUDE.md](CLAUDE.md) is a few lines. It
  `@`-includes [docs/spec.md](docs/spec.md), so every session starts
  from the index and follows pointers from there. System reference
  lives in `docs/`, not in `CLAUDE.md`.

- **Durable `docs/`** — long-lived reference, indexed by
  [docs/spec.md](docs/spec.md). Each doc has an `_Updated: YYYY-MM-DD_`
  line, bumped only for substantive changes. Docs describe what the
  system is; agent behavior stays in `CLAUDE.md`.

- **Dated `mds/`** — `YYYY-MM-DD-name.md` working documents for
  planning, investigations, dead ends. Not authoritative: the date
  prefix says they may be stale. Indexed by [mds/index.md](mds/index.md).
  Convention: [docs/dated-markdown.md](docs/dated-markdown.md).

- **Multi-repo hub** — one repo where sessions start for work that
  spans several sibling repos, with cross-repo notes kept in its
  `mds/`. See [docs/hub.md](docs/hub.md).
