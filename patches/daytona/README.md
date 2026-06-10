# Daytona Source Patches

This directory records source-level Daytona changes carried by this fork.

Deployment overlays, Terraform, cloud-specific configuration, and packaging
scripts are intentionally excluded from this source repository and live in the
private `cori-daytona` infrastructure repository.

Current patches:

- `0001-volume-manager-nonfatal-s3-connection-test.patch`: keep API startup
  running when the S3-compatible volume backend is temporarily unavailable.
- `0002-dashboard-oidc-local-storage.patch`: persist OIDC state in browser
  local storage outside localhost.
- `0003-compose-self-hosted-startup.patch`: relax selected compose startup
  dependencies for the self-hosted/local deployment shape.
- `0004-package-license-metadata.patch`: align root package licence metadata
  with the repository AGPL licence for scanner consistency.
