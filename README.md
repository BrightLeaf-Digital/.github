# BrightLeaf-Digital/.github

Shared GitHub Actions workflows for the BrightLeaf plugin suite.

## Workflows

- **`pcp-check-and-deploy.yml`** — Reusable workflow that runs WordPress Plugin Check (PCP), then deploys to Freemius and/or WordPress.org SVN. Handles namespace prefixing via Strauss, automatic Lite version naming, SVN retry logic, changelog extraction, and documentation sync.
- **`purge-update-feed.yml`** — Weekly scheduled job that purges old entries from the internal update feed API.
