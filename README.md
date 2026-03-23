# ghcp-in-action

[![Use this template](https://img.shields.io/badge/Use%20this%20template-2ea44f?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mburakunuvar/ghcp-in-action-demo/generate)

> Click **"Use this template"** above to create your own copy of this repo and follow along with the demo.

A hands-on live demo showcasing **GitHub Copilot** working across three developer surfaces — the GitHub web UI, your IDE, and your terminal — to build, review, and deploy a mini web application end-to-end.

---

## About This Demo

This demo walks through a realistic developer workflow driven entirely by GitHub Issues. Each issue is assigned to the Copilot tool best suited for the job, demonstrating how the different surfaces complement each other rather than overlap.

By the end of the demo, a small web app has been:
- **Built** (home page, agenda page, labs page)
- **Reviewed** by two AI models with findings filed as new issues
- **Deployed** to Azure via an AI-generated GitHub Actions workflow

---

## GitHub Copilot Surfaces

| Tool | Where | Best for |
|---|---|---|
| **GitHub Coding Agent** | GitHub.com (Issues / PRs) | Async, cloud-based coding tasks kicked off from an issue |
| **Agent Mode** | IDE (VS Code) | Interactive, local workspace tasks with real-time iteration |
| **Copilot CLI** | Terminal | Shell commands, DevOps tasks, and quick code tasks without leaving the terminal |

---

## Prerequisites

Before running this demo, make sure the following are in place:

- A GitHub repository with at least **5 open issues** (Issues 1–5 as described below)
- **GitHub Copilot** enabled on the account and the repository
- **VS Code** with the repo cloned locally and Agent Mode enabled
- **Copilot CLI** installed and authenticated — verify with `gh auth status`
- An **Azure subscription** and deployment target configured (for Issue 5)

---

## Demo Scenarios

### Issue 1 — Home Page
**Tool**: GitHub Coding Agent &nbsp;|&nbsp; **Surface**: GitHub.com

Copilot is assigned the issue directly from the GitHub Issues UI. It autonomously plans and implements a simple front-end home page featuring an event title, a welcome message mentioning Amsterdam, and two navigation buttons (Agenda and Labs). The agent opens a draft PR with its changes and comments on its own progress.

---

### Issue 2 — Agenda Page
**Tool**: Copilot CLI &nbsp;|&nbsp; **Surface**: Terminal

From the terminal, Copilot CLI scaffolds a child Agenda page using a natural language prompt. The suggestion is reviewed, executed, and committed — without ever leaving the command line.

```sh
gh copilot suggest "scaffold an Agenda child page based on the structure in index.html"
```

---

### Issue 3 — Labs Page
**Tool**: Agent Mode &nbsp;|&nbsp; **Surface**: IDE (VS Code)

In VS Code, Agent Mode reads the existing page structure and builds a matching Labs child page. The agent inspects files, proposes edits inline, and can run a local preview to verify the result — all within a single chat conversation.

---

### Issue 4 — Code Review & Performance
**Tool**: Copilot CLI &nbsp;|&nbsp; **Surface**: Terminal

Two AI models review the codebase from different angles:

- **Opus** performs a code quality review (best practices, error handling, accessibility)
- **Codex** performs a performance review (asset optimization, render-blocking resources, caching)

The findings from each review are used to automatically file two new GitHub issues:

```sh
gh issue create --title "Code Quality Improvements" --body "..."
gh issue create --title "Performance Improvements" --body "..."
```

This closes a real-world loop: *AI reviews code → findings become trackable issues → issues can be assigned back to Copilot to fix.*

---

### Issue 6 — Code Quality Improvements *(auto-created)*
**Created by**: Copilot CLI during Issue 4

Tracks code quality findings surfaced by the Opus review. Addressed or explicitly deferred before deployment.

---

### Issue 7 — Performance Improvements *(auto-created)*
**Created by**: Copilot CLI during Issue 4

Tracks performance findings surfaced by the Codex review. Addressed or explicitly deferred before deployment.

---

### Issue 5 — Azure Deployment *(final step)*
**Tool**: Agent Mode &nbsp;|&nbsp; **Surface**: IDE (VS Code)

> **⚠️ Prerequisite**: Issues 1–4, 6, and 7 must all be closed (or explicitly deferred) before deployment begins.

With all issues resolved, Agent Mode is prompted to deploy the application to Azure. The agent inspects the repo for existing CI/CD configuration, generates or updates a GitHub Actions workflow, and triggers the deployment. The live app is verified at the deployed URL.

---

## Quick Reference

| Issue | Task | Tool | Surface |
|---|---|---|---|
| 1 | Home Page | GitHub Coding Agent | GitHub.com |
| 2 | Agenda Page | Copilot CLI | Terminal |
| 3 | Labs Page | Agent Mode | IDE |
| 4 | Code Review & Performance | Copilot CLI | Terminal |
| 6 *(auto-created)* | Code Quality Improvements | Copilot CLI | Terminal |
| 7 *(auto-created)* | Performance Improvements | Copilot CLI | Terminal |
| 5 *(final)* | Azure Deployment | Agent Mode | IDE |

---

## Repo Contents

| File | Description |
|---|---|
| `demo-guide.md` | Full presenter guide with step-by-step instructions and talking points |
| `track-status.md` | Live-updatable checklist to track progress during the demo |
| `README.md` | This file |
