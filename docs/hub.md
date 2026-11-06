---
summary: The multi-repo hub pattern -- one repo where cross-repo sessions start, and the additionalDirectories setting that lets it read its siblings.
---

# The Multi-Repo Hub Pattern

_Updated: 2026-11-06_

One repo (this one) is where sessions start for work that spans
several repos, projects, or subjects. The hub:

1. **Grants the agent read access across sibling repos** via the
   `additionalDirectories` setting, so one session can search and read
   the whole workspace.
2. **Holds dated working documents** (`mds/`) for cross-repo work that
   doesn't belong to any single project.

## additionalDirectories

In `.claude/settings.local.json` (per-user and gitignored, since the
paths depend on where each person keeps their clones):

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

A session started in the hub can then read those paths. Edits still go
through the usual permission flow.

## Why one hub instead of a session per repo

- **Cross-repo investigations** -- a question often touches a service,
  its client, and the deploy config at once. One session keeps that
  context together.
- **Working documents in one place** -- notes for cross-cutting work
  live in the hub's `mds/`, not scattered across project repos.

## What stays in the sibling repo

Each sibling repo keeps its own `CLAUDE.md` and `docs/`. Project-local
conventions, system reference, and project-scoped `mds/` belong there.
The hub is for cross-cutting work.
