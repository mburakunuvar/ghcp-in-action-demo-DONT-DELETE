---
name: "Issue 5 — Code Review and Performance"
about: "AI-powered code review using two models; findings become new issues"
title: "4 - Code Review and Performance"
labels: ""
---

## Task
Perform a code review of the full application:

1. **Code quality review** using Copilot CLI with Opus — focus on best practices, error handling, accessibility
2. **Performance review** using Copilot CLI with Codex — focus on asset optimization, render-blocking resources, caching

The findings from each review should be filed as two new GitHub issues:
- **Issue 7**: Code Quality Improvements (from Opus review)
- **Issue 8**: Performance Improvements (from Codex review)

## Assigned to
Copilot CLI — use `gh copilot suggest` for both reviews, then `gh issue create` to file the findings.
