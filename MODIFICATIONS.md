# Modifications to Daytona

This repository contains Cori Clinical Ltd's modified version of Daytona.

## Summary of Modifications

Cori Clinical Ltd has modified Daytona to support local execution in Cori's
self-hosted sandbox environment. In particular, the modified version runs
locally in a self-hosted deployment with an S3-compatible object storage
service, including MinIO in local compose-based environments.

The current modifications are:

- `apps/api/src/sandbox/managers/volume.manager.ts`: log a warning when the
  S3-compatible storage connection test fails instead of failing API startup.
- `apps/dashboard/src/providers/ConfigProvider.tsx`: use browser
  `localStorage` for OIDC state outside localhost so production sessions remain
  available across page reloads.
- `docker/docker-compose.yaml`: adjust compose startup dependencies for the
  self-hosted/local deployment shape.
- `package.json`: set the root source-distribution licence metadata to
  `AGPL-3.0-only` so scanners align with the repository `LICENSE`.

This supports Cori's local/self-hosted sandbox environment where required
runtime assets or files are not retrieved from AWS S3 in the same way as
vanilla Daytona.

MinIO is not Daytona source code and is not a Cori Clinical Ltd modification to
Daytona. It is a separate S3-compatible object storage service referenced by
the included compose configuration. Cori Clinical Ltd has not modified MinIO
source code or the MinIO container image; compatibility is provided by Daytona
configuration that points the API and runner at a MinIO S3-compatible endpoint.

## Modification History

| Date | Commit/tag | Description |
|---|---|---|
| 2026-06-10 | `prod-2026-06-10` | Applied Cori Clinical Ltd's Daytona modifications on top of upstream Daytona `506730d50c433d397b79b6e0123167fa3cb2ae88`. |

## Production Version

The production source release is identified by the Git tag:

`prod-2026-06-10`

## Licence

Daytona is licensed under AGPL-3.0. Cori Clinical Ltd's modifications to
Daytona are also licensed under AGPL-3.0.

See `LICENSE` for the full licence text.
