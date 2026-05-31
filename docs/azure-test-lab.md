# Azure Test Lab Notes

This fork is part of the Azure Test Lab incident-generation portfolio. It is intended to provide realistic vulnerable web application telemetry for Microsoft Defender and Sentinel demos after the basic build and smoke path is proven.

## Current Lab Workflow

The `Azure Test Lab Smoke` workflow is manual only. It performs a local GitHub Actions validation loop:

1. Build the Juice Shop Docker image from this fork.
2. Run the container bound to `127.0.0.1:3000` on the GitHub-hosted runner.
3. Send benign HTTP requests to `/` and `/rest/products/search?q=apple`.
4. Upload a small smoke report and captured response artifacts.

The workflow does not deploy to Azure, expose a public endpoint, run attack traffic, or mutate lab resources.

## Next Implementation Steps

- Add an Azure deployment wrapper only after the local smoke workflow is stable.
- Prefer a private endpoint or tightly scoped lab-only access path for any hosted deployment.
- Keep scripted traffic allowlisted and documented before using it for Defender or Sentinel demos.
- Record workflow run IDs and any generated telemetry in the control-plane lab documentation.