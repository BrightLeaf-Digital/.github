# BrightLeaf-Digital/.github

Shared GitHub Actions workflows for the BrightLeaf plugin suite.

## Workflows

- **`deploy.yml`** — Reusable workflow that deploys to Freemius and/or WordPress.org SVN after the local release gate. Handles namespace prefixing via Strauss, automatic Lite version naming, SVN retry logic, changelog extraction, and documentation sync. Reports deployment milestones to the GravityOps Release Service; the final successful Slack message includes that version's changelog from the released commit's `readme.txt`. Missing changelogs or notification failures do not fail the release.
- **`purge-update-feed.yml`** — Weekly scheduled job that purges old entries from the internal update feed API.

The backend's `BLD_RELEASE_SLACK_CHANNEL` constant selects the Slack destination; no Slack credentials or destination IDs are passed by the workflow. The Slack bot must have access to the destination channel.
