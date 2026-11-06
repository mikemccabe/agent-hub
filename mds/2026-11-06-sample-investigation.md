---
summary: >-
  Illustrative entry showing the format: a slow checkout page traced
  across the web, api and infra repos to a smaller connection pool. Open.
---

# 2026-11-06 Sample investigation: slow checkout page

_A sample `mds/` entry. Not a real investigation; it shows the shape of
a working document and how one hub session spans sibling repos._

## Context

Checkout page load time crept up over the past week. Goal: find whether
the regression is in the page, the API behind it, or the deploy.

## What I looked at (cross-repo)

1. **`../web`** -- the checkout page renders the same; no change to its
   bundle since the slowdown began.
2. **`../api`** -- the cart endpoint's response time stepped up on one
   date, matching the slowdown.
3. **`../infra`** -- a config change the same day lowered the API's
   connection pool size.

## Hypothesis

The smaller pool queues cart requests under peak load. Need to confirm
by comparing request queue time before and after the change.

## Status

Open. Next step: restore the old pool size on one instance and compare.
