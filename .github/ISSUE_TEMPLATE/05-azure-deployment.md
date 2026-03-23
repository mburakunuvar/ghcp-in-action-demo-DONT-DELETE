---
name: "Issue 5 — Azure Deployment"
about: "Trigger a final deployment to verify the live app (final step)"
title: "Azure Deployment"
labels: ""
---

## Task
The application is already deployed to Azure Static Web Apps and a CI/CD workflow is in place (`.github/workflows/azure-static-web-apps.yml`).

For this final step:
1. Confirm all previous issues (1, 2, 3, 4, 6, 7) are closed
2. Verify the latest changes are live at the deployed URL
3. If anything needs to be re-triggered, use Agent Mode to run the workflow

> ⚠️ **Prerequisite**: This issue must only be started after Issues 1, 2, 3, 4, 6, and 7 are all closed (or explicitly deferred). Deployment is the final gate.

## Assigned to
Agent Mode in IDE (VS Code) — prompt: *"All issues are resolved. Verify the app is deployed and the live site reflects all the latest changes. Trigger a re-deployment if needed."*

## Pre-flight requirement
The presenter must have already:
- Created an Azure Static Web App connected to this repository
- Added `AZURE_STATIC_WEB_APPS_API_TOKEN` to the repository secrets
