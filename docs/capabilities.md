---
summary: >-
  What a session can reach from here beyond the files in the repos
  (signed-in tools, connectors, accounts, other machines), as a table of
  goals, each with the way in and the catch. Covers: nothing yet.
updated: 2026-11-14
---

# Capabilities

What a session started in this hub can reach beyond the files in the
repos: a command-line tool that is signed in, a connector (an MCP
server), an account, another machine. Nothing in the repos says these
are there, so without a note a session concludes there is no way in,
or takes the long way round. This page is that note, and the only
record of it.

An entry earns its place when a session would otherwise get it wrong.
What any session finds on its own -- the files, git, the tools it
starts with -- is not listed.

## What an entry holds

- **The goal, in the words of someone who wants it:** "see what is
  deployed", not the name of the system that answers. A search under
  the system's name misses the entry.
- **The way in, and the catch:** the command, connector or account,
  then whatever would otherwise read as "can't": only on one machine,
  only on the VPN, read-only, a second account. Literal names, since
  the page is searched as often as it is read.
- **Where the detail is:** a page or an md, when there is one. An
  entry stays a line or two; one that keeps growing is missing its
  page.
- **Where a password or token is kept, never the secret itself:** a
  password manager entry, the keychain, a file outside the repo.
- **The day it was checked, where that matters:** access lapses
  without notice.

A known "no" is an entry too: what is not available, the check that
showed it and the day, so that a session neither tries it again nor
takes it as permanent. When the answer changes, the entry is
rewritten or removed.

Lookups that belong to one subject stay on that subject's page, in a
section such as "Where to look"; this page holds the way in and points
there. Other repos go by name, and an entry names a machine only when
reach differs from one machine to another.

The form, with made-up rows:

```markdown
| Goal | The way in, and the catch | Detail |
|------|---------------------------|--------|
| **See what is deployed** | `gh run list` in `infra`. The GitHub CLI is signed in on the laptop only | "Where to look" in [shop.md](shop.md) |
| **Read team chat** | The chat connector: channels, threads, search. Read-only: it cannot post | -- |
| **Query orders** | `psql` against the read-only copy, on the VPN only. The password is in the password manager under "shop read-only". Checked 2026-11-06 | [slow-checkout](../mds/2026-11-06-slow-checkout.md) |
| **Send mail** | Not available (checked 2026-11-06): the mail connector reads and drafts but does not send | -- |
```

## Entries

The table is the whole record: a fact about access goes in as a row,
not as a paragraph under it. The `summary:` at the top of this page
ends with the kinds of thing covered ("Covers: team chat, deploys"),
so that the docs index, which every session loads, shows what is here.

| Goal | The way in, and the catch | Detail |
|------|---------------------------|--------|
