---
name: "Issue 6 — Azure Deployment"
about: "Verify and trigger final deployment (final step)"
title: "Azure Deployment"
labels: ""
---

## Task
The application is already deployed to Azure Static Web Apps and a CI/CD workflow is in place (`.github/workflows/azure-static-web-apps.yml`).

For this final step:
1. Confirm all previous issues (2, 3, 4, 5, 7, 8) are closed
2. Verify the latest changes are live at the deployed URL
3. If anything needs to be re-triggered, use Agent Mode to run the workflow

> ⚠️ **Prerequisite**: This issue must only be started after Issues 2, 3, 4, 5, 7, and 8 are all closed (or explicitly deferred). Deployment is the final gate.

## Assigned to
Agent Mode in IDE (VS Code) — prompt: *"All issues are resolved. Verify the app is deployed and the live site reflects all the latest changes. Trigger a re-deployment if needed."*

## Pre-flight requirement
The presenter must have already completed Issue 1 (Azure Static Web App Setup) before the demo:
- Azure Static Web App created and connected to this repository
- `AZURE_STATIC_WEB_APPS_API_TOKEN` added to the repository secrets
