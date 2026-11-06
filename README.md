# agent-hub

A starting point for a personal hub repo: the place where you start
coding-agent sessions (Claude Code here) and where their context lives
as plain files under git. A short `CLAUDE.md`, durable `docs/`, dated
`mds/`, and generated indexes.

LLM interactions are ultimately personal: what one person finds useful,
another finds noise. Many context-management tools ship each week; the
mechanism here is just the filesystem. Take this as a base and make it
yours.

## Start your own

Copy it rather than forking it. The copy is yours, with its own
history; nothing here expects changes to flow back.

```sh
git clone --depth 1 <this-repo-url> my-hub
cd my-hub
rm -rf .git && git init
git config core.hooksPath .githooks
git add -A && git commit -m "Start from agent-hub"
```

`core.hooksPath` turns on the hook that keeps the indexes current. It
is per clone, so set it again on any other machine you clone your hub
to. The hook needs `python3` (standard library only).

Then:

1. Rewrite the top of [CLAUDE.md](CLAUDE.md) and
   [docs/spec.md](docs/spec.md) to say what your hub is for.
2. List your sibling repos in `.claude/settings.local.json` (see
   [docs/hub.md](docs/hub.md)).
3. Delete the sample working document in `mds/` once you have your
   own, or keep it as a format reference.

Push to a private remote of your own: the record is only yours if it
lives somewhere you control.

## What's here

- **Short `CLAUDE.md`** — a few lines. It `@`-includes
  [docs/spec.md](docs/spec.md) and [docs/index.md](docs/index.md), so
  every session starts from the overview and the doc list and follows
  pointers from there. System reference lives in `docs/`, not in
  `CLAUDE.md`.

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
  `bin/md-index`, run by the git pre-commit hook. Convention:
  [docs/dated-markdown.md](docs/dated-markdown.md).

- **Multi-repo hub** — sessions for work that spans several sibling
  repos start here, with cross-repo notes kept in `mds/`. See
  [docs/hub.md](docs/hub.md).
