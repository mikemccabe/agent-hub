---
summary: >-
  The shop: the three repos behind the store (web, api, infra),
  what each is, and where to look for deploys, dashboards, owners and
  settings. A sample page.
updated: 2026-11-06
---

# The shop

_A sample `docs/` page. Not a real system; it shows the shape of a
durable page: what exists and where to look, with status and history
left to dated mds. Delete it once you have pages of your own._

The store is three repos; [hub.md](hub.md) has the setting that lets
a session read them.

| Repo | What it is |
|------|------------|
| `web` | The storefront: pages, the checkout flow, the browser bundle |
| `api` | The HTTP API behind the storefront: cart, orders, accounts. Talks to the database through a connection pool |
| `infra` | Deploy configuration for both, and the dashboards |

## Where to look

- **What is deployed:** the deploy pipeline's run list in `infra`,
  newest first.
- **How it is doing:** the "Shop" dashboard, linked from `README.md`
  in `infra`: page load and API response times per region.
- **Who owns what:** the `CODEOWNERS` file in each repo.
- **Limits and settings** (pool sizes, timeouts, rate limits): set in
  `infra`. Search there rather than copying values here.

## Working on it

Cross-repo questions start in this hub, with a dated md when a finding
is worth keeping. In flight:
[slow-checkout](../mds/2026-11-06-slow-checkout.md).
