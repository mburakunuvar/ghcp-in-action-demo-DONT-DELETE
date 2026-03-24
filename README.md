# ghcp-in-action

[![Use this template](https://img.shields.io/badge/Use%20this%20template-2ea44f?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mburakunuvar/ghcp-in-action-demo-DONT-DELETE/generate)

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

- A GitHub repository with **7 issues** (auto-created on first push by the setup workflow; 6 remain open after closing Issue 1)
- **Issue 1 completed and closed** — Azure Static Web App created, `AZURE_STATIC_WEB_APPS_API_TOKEN` added to repo secrets, and the live URL verified
- **GitHub Copilot** enabled on the account and the repository
- **VS Code** with the repo cloned locally and Agent Mode enabled
- **Copilot CLI** installed and authenticated — verify with `gh auth status`

> 🎬 **The live demo starts at Issue 2.** Issue 1 is pre-work done before going on stage.

---

## Demo Scenarios

### Issue 1 — Azure Static Web App Setup *(pre-demo)*
**Tool**: Azure Portal / az CLI &nbsp;|&nbsp; **When**: Before the demo

Done before going on stage. Create an Azure Static Web App, connect it to the repo, add `AZURE_STATIC_WEB_APPS_API_TOKEN` to repo secrets, and verify the live URL. The blank pages deploy automatically on the first push — the URL is live and visible to the audience from the moment the demo begins.

---

### Issue 2 — Scaffold and Beautify the Home Page
**Tool**: GitHub Coding Agent &nbsp;|&nbsp; **Surface**: GitHub.com

Copilot is assigned the issue directly from the GitHub Issues UI. The blank `index.html` already exists — the agent scaffolds and beautifies it with an event title, a welcome message mentioning Amsterdam, and two navigation buttons linking to `agenda.html` and `labs.html`. The agent opens a draft PR with its changes and comments on its own progress.

---

### Issue 3 — Agenda Page
**Tool**: Copilot CLI &nbsp;|&nbsp; **Surface**: Terminal

From the terminal, Copilot CLI scaffolds a child Agenda page using a natural language prompt. The suggestion is reviewed, executed, and committed — without ever leaving the command line.

```sh
gh copilot suggest "scaffold an Agenda child page based on the structure in index.html"
```

---

### Issue 4 — Labs Page
**Tool**: Agent Mode &nbsp;|&nbsp; **Surface**: IDE (VS Code)

In VS Code, Agent Mode reads the existing page structure and builds a matching Labs child page. The agent inspects files, proposes edits inline, and can run a local preview to verify the result — all within a single chat conversation.

---

### Issue 5 — Azure Deployment
**Tool**: Agent Mode &nbsp;|&nbsp; **Surface**: IDE (VS Code)

> **⚠️ Prerequisite**: Issues #2 (Home Page), #3 (Agenda Page), and #4 (Labs Page) must be closed before deployment. Code Review happens after this step.

The app is **already live** from the first push (Issue 1). Issue 5 is the deployment verification: Agent Mode confirms Issues 2–4 are closed, checks the existing `.github/workflows/azure-static-web-apps.yml` workflow, triggers a final deployment if needed, and the audience sees the fully built app at the live URL.

---

### Issue 6 — Code Review & Performance
**Tool**: Copilot CLI &nbsp;|&nbsp; **Surface**: Terminal

Two AI models review the live deployed app from different angles:

- **Opus** performs a code quality review (best practices, error handling, accessibility)
- **Codex** performs a performance review (asset optimization, render-blocking resources, caching)

The findings from each review are filed as two new GitHub issues with short, pre-written bodies — ready to run as-is, no copy-pasting on stage:

```sh
gh issue create --title "Fix: missing alt attributes and semantic HTML" --body "Flagged by Copilot code review (Opus): ..."
gh issue create --title "Fix: render-blocking CSS and missing meta tags" --body "Flagged by Copilot performance review (Codex): ..."
```

These two issues are then addressed using **`/fleet`** in Copilot CLI, which hands them off to the GitHub Coding Agent directly from the terminal.

This closes a real-world loop: *AI reviews the live app → findings become trackable issues → issues are handed off to Copilot to fix.*

---

### Fix: missing alt attributes and semantic HTML *(auto-created)*
**Created by**: Copilot CLI during Issue 6 &nbsp;|&nbsp; **Addressed by**: `/fleet` in Copilot CLI

Tracks code quality findings surfaced by the Opus review. Handed off to the GitHub Coding Agent via `/fleet` for a quick fix.

---

### Fix: render-blocking CSS and missing meta tags *(auto-created)*
**Created by**: Copilot CLI during Issue 6 &nbsp;|&nbsp; **Addressed by**: `/fleet` in Copilot CLI

Tracks performance findings surfaced by the Codex review. Handed off to the GitHub Coding Agent via `/fleet` for a quick fix.

---

## Quick Reference

| Issue | Task | Tool | Surface |
|---|---|---|---|
| 1 *(pre-demo)* | Azure Static Web App Setup | Azure Portal / az CLI | — |
| 2 | Scaffold & Beautify Home Page | GitHub Coding Agent | GitHub.com |
| 3 | Agenda Page | Copilot CLI | Terminal |
| 4 | Labs Page | Agent Mode | IDE |
| 5 | Azure Deployment | Agent Mode | IDE |
| 6 | Code Review & Performance | Copilot CLI | Terminal |
| *(auto-created)* | Fix: missing alt attributes and semantic HTML | GitHub Coding Agent (via `/fleet`) | Terminal |
| *(auto-created)* | Fix: render-blocking CSS and missing meta tags | GitHub Coding Agent (via `/fleet`) | Terminal |

---

## Repo Contents

| File | Description |
|---|---|
| `README.md` | This file |
| `index.html` | Blank home page scaffold |
| `agenda.html` | Blank agenda page scaffold |
| `labs.html` | Blank labs page scaffold |
| `template-agenda.txt` | Agenda content template (referenced by Issue #3) |
| `template-labs.txt` | Labs content template (referenced by Issue #4) |
| `template-azureapp.md` | Reusable runbook for Azure Static Web App setup (Issue #1) |
| `.github/workflows/setup-issues.yml` | Auto-creates issues and labels on first push |
| `.github/workflows/azure-static-web-apps.yml` | Manual-trigger deployment to Azure Static Web Apps |
