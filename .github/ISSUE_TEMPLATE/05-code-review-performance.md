---
name: "Issue 5 — Code Review and Performance"
about: "AI-powered code review using two models; findings become new issues"
title: "Code Review and Performance"
labels: "copilot-cli"
---

## Task
Perform a code review of the full application:

1. **Code quality review** using Copilot CLI with Opus — focus on best practices, error handling, accessibility
2. **Performance review** using Copilot CLI with Codex — focus on asset optimization, render-blocking resources, caching

The findings from each review should be filed as two new GitHub issues:
- **Code Quality Improvements** (from Opus review)
- **Performance Improvements** (from Codex review)

## Assigned to
Copilot CLI — use `gh copilot suggest` for both reviews, then `gh issue create` to file the findings.

## Important: Issue body format
When creating the Code Quality and Performance issues, include a `## Completion` section at the end of each issue body with a `gh issue close <NUMBER>` command (using the issue number returned by `gh issue create`) so Copilot CLI knows to close the issue when done.

## Completion
Once the Code Quality and Performance issues are created and filed, close this issue:

```bash
gh issue close 5 --repo <owner/repo>
```
