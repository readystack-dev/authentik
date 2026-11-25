# authentik 2026.8.5 — ReadyStack release `2026.8.5-CE-ubuntu24.04-r8`

Generated 2026-11-25 from this release's build records and strategy. Statements that come from a single record name it in brackets; the others come from this release's strategy and build log.

## Release

- **Image:** `readystack/authentik:2026.8.5-CE-ubuntu24.04-r8` (linux/amd64). Index digest `sha256:7007d435e8f01070244a37872dbefed0acaca1d466764ba6ed557aee073c2690` [`docs/provenance/LOCKED_DIGEST.txt`].
- **Image manifest digest:** `sha256:ca993b4c57f308d8769039d6124cdc0151ad7fa279d2439a009be0b623cd819b` [`TARGET_DIGEST.txt`].
- **Upstream:** authentik 2026.8.5 built from source at `version/2026.8.5` of https://github.com/goauthentik/authentik — upstream notes: https://github.com/goauthentik/authentik/releases/tag/version/2026.8.5 [`docs/provenance/BUILD_RECIPE.json`].
- **Base image:** `ubuntu:24.04`; runtime user `authentik`.
- **Build:** `source-rebuild-python`, compiled offline with `--network=none`.
- **Supersedes:** ReadyStack release `2026.8.5-CE-ubuntu24.04-r7`.

## What changed in this release

- Upstream version unchanged (2026.8.5); ReadyStack rebuild.
- authentik 2026.8.5 is unchanged from the release this supersedes (2026.8.5-CE-ubuntu24.04-r7); this release rebuilds it. Changes: libssh-4 moves from 0.10.6-2ubuntu0.5 to 0.10.6-2ubuntu0.6 (USN-9187-1). Settings, ports and data volumes are those of 2026.8.5-CE-ubuntu24.04-r7: replace the container with this image on the same volumes.

## Security status at release (measured 2026-11-25)

- **Docker Scout:** 0 fixable critical/high vulnerabilities after 1 OpenVEX statement of ours (`docs/security/VEX.openvex.json`; Docker Scout's default policy does not read them and counts it as fixable); runs as `1000` (non-root); SBOM + provenance attestations present (SPDX SBOM + SLSA v1) [`docs/provenance/SCOUT_VERDICT.json`].
- **OSV cross-check:** no fixable critical/high vulnerability beyond Docker Scout's findings.
- **Signature:** cosign signature verified by ReadyStack's release gate before publishing; check it yourself with `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/authentik:2026.8.5-CE-ubuntu24.04-r8` (signatures are recorded in the public Sigstore transparency log).
- **ReadyStack release check at release:** passed (ReadyStack's own test, not a Docker Scout grade). Vulnerabilities are disclosed every day and the image never changes, so it is re-checked daily, beside Docker Scout's own dated grade, at https://readystack.dev/queue.
- **Before exposing this service:** Until akadmin has a password, anyone who can reach /if/flow/initial-setup/ can set it: set AUTHENTIK_BOOTSTRAP_PASSWORD at first start, or finish that setup before exposing the instance.

## Reproducibility

Rebuilds offline from this archive to the identical image digest `sha256:ca993b4c57f308d8769039d6124cdc0151ad7fa279d2439a009be0b623cd819b`: run `./BUILD_OFFLINE.sh`, then `./VERIFY_OFFLINE.sh` (add `--online` to confirm the Docker Hub tag holds the same digest). Before publishing, ReadyStack rebuilt the kit with `./BUILD_OFFLINE.sh` and compared the result with the published digest [`docs/provenance/REPRO_VERIFICATION.json`], then ran `./BUILD_OFFLINE.sh` and `./VERIFY_OFFLINE.sh` from this archive (without `--online`).

## Validation

- 3 of 3 use cases passed (3 authored) against the running image [`docs/validation/test-results.json`].
- The cases are `GET /-/health/live/` (200), `GET /-/health/ready/` (200), `GET /api/v3/root/config/` (200); the suite checks nothing else.

## Known issues

- **high** (upstream): First visitor can claim the administrator account until setup is completed [`RSD-authentik-f2fc0642db`]

## Verify this archive

```
sha256sum -c CHECKSUMS.sha256
./BUILD_OFFLINE.sh && ./VERIFY_OFFLINE.sh --online
cosign verify --key https://readystack.dev/keys/cosign.pub readystack/authentik:2026.8.5-CE-ubuntu24.04-r8
```

ReadyStack records every signature in the public Sigstore transparency log (Rekor), so the command needs no extra flags.

