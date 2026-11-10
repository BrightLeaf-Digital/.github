# BrightLeaf-Digital/.github

Shared GitHub Actions workflows for the BrightLeaf plugin suite.

## Workflows

- **`deploy.yml`** — Reusable workflow that deploys to Freemius and/or WordPress.org SVN after the local release gate. A caller passes only its `product_id`; the workflow reads that product's authenticated release configuration from the GravityOps Release Service (`/gravityops/v1/release-config/{product_id}`), validates it, and refuses a record that belongs to another repository. The distribution slug, Freemius product, channels, WordPress.org slug and docs-sync choice all come from that record. Handles namespace prefixing via Strauss, automatic Lite version naming, SVN retry logic, documentation sync and release recording (`/gravityops/v1/releases`). A rejected docs sync or release record fails the run. Deployment milestones go to `/gravityops/v1/notifications/release`; the final successful Slack message includes that version's changelog from the released commit's `readme.txt`. Missing changelogs or notification failures do not fail the release.
- **`wporg-assets.yml`** — Reusable workflow that mirrors a plugin's `.wordpress-org/` assets to WordPress.org SVN. Callers pass `product_id`; the WordPress.org slug comes from the same release configuration.
- **`purge-updates-feed.yml`** — Retired. Its weekly schedule is removed because the Release Service filters recent updates by timestamp and reconciles projections daily. It remains runnable by hand until the legacy route is retired.

Callers pass the `BLD_API_KEY` secret to both reusable workflows. `UPDATE_FEED_URL` is no longer used.

The backend's `BLD_RELEASE_SLACK_CHANNEL` constant selects the Slack destination; no Slack credentials or destination IDs are passed by the workflow. The Slack bot must have access to the destination channel.
