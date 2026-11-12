# agent-hub

See @docs/spec.md for what this hub is and @docs/index.md for the docs.
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

## Committing

A doc is part of the record once it is committed, and the indexes
update on commit. When a change to `docs/` or `mds/` is complete,
commit it without asking. Commit by pathspec
(`git commit -m ... -- <paths>`), so only the files of this change go
in. An md made with `/md` is committed as it is created.

Git needs an author name and email. Before the first commit of a
session, check `git config user.name` and `git config user.email`. If
either is empty, ask the user once which name and email to use. Say
that real ones are optional, and offer the placeholder (`Hub User`,
`hub@example.com`) if they prefer. Then set both for this repo with
`git config user.name` and `git config user.email`. Once set, don't
raise it again.

## Writing in docs/

Before adding a number, a list, a version, a status line or a bit of
history to a `docs/` page, apply "Keeping churn out of docs/" in
[docs/dated-markdown.md](docs/dated-markdown.md): where to look rather
than the answer, scale rather than a count, status and history in an
md.

## Other repos

Refer to the other repos by name (`api`), not by path on disk: where
each one lives is per machine, set in `.claude/settings.local.json`
([docs/hub.md](docs/hub.md)).

## Doc timestamps

Long-lived docs under `docs/` carry an `_Updated: YYYY-MM-DD_` line
right after the H1. Bump it for substantive revisions only, not for
typo fixes, link tweaks or formatting; see "docs/" in
[docs/dated-markdown.md](docs/dated-markdown.md).
