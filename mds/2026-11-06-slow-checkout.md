---
summary: >-
  Why the checkout page got slow: traced across the web, api and infra
  repos to a smaller API connection pool. Open; next is to restore the
  pool size on one instance and compare. A sample md.
---

# 2026-11-06 Slow checkout page

_A sample `mds/` entry. Not a real investigation; it shows the shape of
a working document and how one hub session spans several repos. Delete
it once you have your own._

## Context

Checkout page load time crept up over the past week. Goal: find whether
the regression is in the page, the API behind it, or the deploy. The
repos are mapped in [the shop](../docs/shop.md).

## What I looked at (cross-repo)

1. **`web`** -- the checkout page renders the same; no change to its
   bundle since the slowdown began.
2. **`api`** -- the cart endpoint's response time stepped up on one
   date, matching the slowdown.
3. **`infra`** -- a config change the same day lowered the API's
   connection pool size.

## Hypothesis

The smaller pool queues cart requests under peak load. Need to confirm
by comparing request queue time before and after the change.

## Status

Open. Next step: restore the old pool size on one instance and compare.
