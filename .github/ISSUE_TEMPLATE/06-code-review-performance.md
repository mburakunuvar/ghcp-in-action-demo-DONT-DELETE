---
name: "Issue 6 — Code Review and Performance"
about: "AI-powered code review of the live deployed app; findings become new issues"
title: "Code Review and Performance"
labels: "copilot-cli"
---

## Task
Perform a code review of the full application (targeting the live deployed app):

1. **Code quality review** using Copilot CLI with Opus — focus on best practices, error handling, accessibility
2. **Performance review** using Copilot CLI with Codex — focus on asset optimization, render-blocking resources, caching

The findings from each review should be filed as two new GitHub issues using pre-written commands (no copy-pasting needed):
- Fix: missing alt attributes and semantic HTML
- Fix: render-blocking CSS and missing meta tags

## Assigned to
Copilot CLI — use `gh copilot suggest` for both reviews, then `gh issue create` to file the findings.

## Note
This step happens after Azure Deployment (#5). The reviews target the live deployed app.

## Completion
Once the findings issues are created and filed, close this issue:

```bash
gh issue close 6 --repo <owner/repo>
```
