# PanelApp Production Release Checklist

Use this checklist for every technician-facing release.

## Before publishing

- [ ] Release is approved from the private `APSInteractive/APS-PanelApp` repository.
- [ ] Windows PowerShell 5.1 parser validation passes.
- [ ] Required PanelApp regression/acceptance tests pass.
- [ ] Real OPS field validation is complete for the release scope.
- [ ] `ScriptVersion` matches the intended release version.
- [ ] Release package contains only files intended for technician deployment.
- [ ] No credentials, tokens, passwords, private keys, field data, logs, or backend source are included.

## Publish the asset first

- [ ] Build `PanelApp-<version>.zip` using the approved release builder.
- [ ] Record the generated ZIP SHA-256 value.
- [ ] Create the GitHub Release/tag `v<version>` in this repository.
- [ ] Upload `PanelApp-<version>.zip` as the release asset.
- [ ] Verify the asset downloads successfully without GitHub authentication.
- [ ] Recalculate the downloaded ZIP SHA-256 and confirm it matches the build output.

## Activate production last

- [ ] Confirm the release asset URL is final and correct.
- [ ] Update `production/manifest.json` with the new version, package URL, SHA-256, and publication timestamp.
- [ ] Keep `forceInstall` false unless an emergency deployment specifically requires it.
- [ ] Verify the raw production manifest is publicly readable.
- [ ] Test one technician launcher against the manifest before broader use.
- [ ] Test one OPS through launch, cache, staging, reboot/resume if applicable, and terminal cleanup.

## Rollback

If a release must be withdrawn, do not delete technician state or bypass PanelApp reconciliation safeguards. Publish/activate a tested replacement release or deliberately point the production manifest back to an approved known-good version after validating the rollback path.
