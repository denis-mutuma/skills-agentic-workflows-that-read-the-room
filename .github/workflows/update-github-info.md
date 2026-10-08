---
name: update-github-info
description: Keep the GitHub Info page current with practical updates from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
    title-prefix: "[github-info] "
---

# Update GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` before making any changes.

Use the web-fetch tool to read these sources:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Select only recent developments that are practical and useful to developers and fit the site's existing editorial angle. Do not repeat information already covered unless a meaningful update is available. Keep summaries short, factual, and actionable; include a direct source link for every addition and identify whether it came from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows. Do not infer details that the source pages do not support.

Update only `site/content/github-info.md`, preserving its existing structure and unrelated content. Review the final diff and verify every new statement against its linked official source. If there is no meaningful, verifiable update, leave the page unchanged and do not open an empty pull request.

When the page changes, use the `create-pull-request` safe output to open one pull request for Mona to review. Give it a concise title and describe the updates and their official source links in the pull request body. Do not write directly to the repository's default branch or use any other mechanism to publish changes.