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

On GitHub, **Use this template** at the top of the repo page makes the
copy, or from a terminal:

```sh
gh repo create my-hub --template mikemccabe/agent-hub --private --clone
```

Anywhere else, clone and start a fresh history:

```sh
git clone --depth 1 https://github.com/mikemccabe/agent-hub my-hub
cd my-hub
rm -rf .git && git init
git add -A && git commit -m "Start from agent-hub"
```

Either way, enable the hooks that keep the indexes current:

```sh
git config core.hooksPath .githooks
```

Hooks are per clone, so repeat that on any other machine you clone your
hub to. The pre-commit hook needs Python 3, found as `python3` or
`python` on your PATH; nothing beyond the standard library. On a Mac,
git and `python3` both come with the Xcode Command Line Tools:
`xcode-select --install`.

Then:

1. If you have sibling repos, list them in
   `.claude/settings.local.json` (see [docs/hub.md](docs/hub.md)). The
   file is yours alone and is gitignored.
2. Consider turning off the agent's own memory, so that findings land
   in `mds/` where they are tracked ("Agent memory" in
   [docs/dated-markdown.md](docs/dated-markdown.md)).
3. Delete the two sample files, [docs/shop.md](docs/shop.md) and
   [mds/2026-11-06-slow-checkout.md](mds/2026-11-06-slow-checkout.md),
   once you have your own, or keep them as format references.

A remote is optional; the clone path above works without one. If you
keep one, make it private and your own: the record stays yours only if
it lives somewhere you control.

## What's here

- **Short `CLAUDE.md`** -- it `@`-includes [docs/spec.md](docs/spec.md)
  and [docs/index.md](docs/index.md), so every session starts from the
  overview and the doc list and follows pointers from there. Reference
  lives in `docs/`, not in `CLAUDE.md`.

- **Durable `docs/`** -- long-lived reference. Each doc has an
  `_Updated: YYYY-MM-DD_` line, bumped only for substantive changes.
  Docs describe how things are; agent behavior stays in `CLAUDE.md`.

- **Dated `mds/`** -- `YYYY-MM-DD-name.md` working documents for
  planning, investigations, dead ends. Not authoritative: the date
  prefix says they may be stale.

- **Generated indexes** -- each doc's frontmatter `summary:` is its
  index entry; [docs/index.md](docs/index.md) and
  [mds/index.md](mds/index.md) are built from those by
  `bin/md-index`, run by the git pre-commit hook. Convention:
  [docs/dated-markdown.md](docs/dated-markdown.md).

- **`/md` skill** -- "make an md" or `/md` creates a dated working
  document and commits it. The skill is a few lines; the convention it
  follows lives in [docs/dated-markdown.md](docs/dated-markdown.md).

- **Multi-repo hub** -- sessions for work that spans several sibling
  repos start here, with cross-repo notes kept in `mds/`. See
  [docs/hub.md](docs/hub.md).
