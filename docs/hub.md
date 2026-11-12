---
summary: The multi-repo hub pattern -- one repo where cross-repo sessions start, and the additionalDirectories setting that lets it read the other repos you work with.
updated: 2026-11-11
---

# The Multi-Repo Hub Pattern

One repo (this one) is where sessions start for work that spans
several repos, projects, or subjects. The hub:

1. **Grants the agent read access to the other repos you work with**
   via the `additionalDirectories` setting, so one session can search
   and read all of them.
2. **Holds dated working documents** (`mds/`) for cross-repo work that
   doesn't belong to any single project.

## additionalDirectories

In `.claude/settings.local.json` (per-user and gitignored, since the
paths depend on where each person keeps their clones). In this example
the repos happen to sit beside the hub:

```json
{
  "permissions": {
    "additionalDirectories": [
      "../api",
      "../web",
      "../infra"
    ]
  }
}
```

Where they live does not matter. Each entry is a path -- absolute,
`~/`, or relative to the hub -- to a repo or any other directory, and
covers everything under it.

A session started in the hub can then read those paths. Edits still go
through the usual permission flow. [shop.md](shop.md) is a sample page
mapping such a set of repos.

Docs and mds refer to the other repos by name (`api`, `infra`), not by
path: the path is each machine's own business, and
`.claude/settings.local.json` is the one place it is written down.

## Why one hub instead of a session per repo

- **Cross-repo investigations** -- a question often touches a service,
  its client, and the deploy config at once. One session keeps that
  context together.
- **Working documents in one place** -- notes for cross-cutting work
  live in the hub's `mds/`, not scattered across project repos.

## What stays in each repo

Each repo keeps its own `CLAUDE.md` and `docs/`. Project-local
conventions, system reference, and project-scoped `mds/` belong there.
The hub is for cross-cutting work.
