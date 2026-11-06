# agent-hub

A sample hub repo showing one way to organize context for a coding
agent: a short `CLAUDE.md`, durable `docs/`, and dated `mds/`.

See @docs/spec.md for overview.

## Doc timestamps

Long-lived docs under `docs/` carry an `_Updated: YYYY-MM-DD_` line as the
second line of the file (right after the H1, blank line on each side).

Bump the date for substantive revisions — new sections, factual
corrections, structural rewrites. Do not bump it for typo fixes, link
tweaks, or formatting-only changes. ISO format.

This convention applies to `docs/` only. Working documents under `mds/`
already encode their date in the filename. Full convention in
[docs/dated-markdown.md](docs/dated-markdown.md).
