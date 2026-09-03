# APS PanelApp Releases

Public distribution repository for **approved APS PanelApp technician releases**.

The private development/source repository remains `APSInteractive/APS-PanelApp`. This repository is intentionally limited to field-deployment metadata and approved release assets.

## Purpose

PanelApp technicians use a stable launcher that checks the production manifest in this repository for an approved version. When a newer approved release is published, the launcher downloads the corresponding GitHub Release ZIP, verifies its SHA-256 hash, caches it on the technician media/device, and stages a temporary working copy on the OPS.

## Production manifest

The technician launcher will eventually read:

`production/manifest.json`

The production manifest is the **final release switch**. Do not update it until the corresponding GitHub Release asset has been uploaded and validated.

## Release order

1. Finish and validate the release in the private `APS-PanelApp` repository.
2. Build the versioned release ZIP and SHA-256 manifest data.
3. Create the matching GitHub Release/tag here.
4. Upload the release ZIP.
5. Verify the release asset can be downloaded and its SHA-256 matches.
6. Update `production/manifest.json` **last**.

## Security boundary

This repository is public. Never commit or upload:

- GitHub personal access tokens or other credentials;
- passwords or service-account secrets;
- production activation keys or private certificates;
- a real `config.json` containing secret values;
- Apps Script/backend source code;
- development source, tests, internal architecture documents, or field data;
- technician/user information, panel inventory exports, logs, or queued events.

Only approved deployment assets intended to be publicly readable should be published here.

## Current status

No production PanelApp release has been activated yet. The initial `production/manifest.json` is an inactive `0.0.0` placeholder and must not be used as the technician update endpoint until the first approved release is published.
