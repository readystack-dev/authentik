# Provenance — authentik (`2026.8.7-CE-ubuntu24.04-r1`)

Every item below is copied from a record in this archive; the record is named in brackets.

## Source

- Upstream repository: https://github.com/goauthentik/authentik
- Revision built: `version/2026.8.7` (commit `37f6d5ecba4c29ad63bb60b1f0fe742560dcb050`)
- Source tree: `5a84e38caef9abd47dc8b10bd7bfa656a4aaa10744d5c147243fac6dbd18db14` over 6153 files [`docs/provenance/SOURCE_TREE_HASH.json`]
- Community Edition only: enterprise code is removed or refused before the build (CE audit at acquire).

## Build

- Method: `source-rebuild-python`; base image `ubuntu:24.04`
- Compiled with `--network=none` from vendored source, dependencies and base images; BuildKit pinned to `moby/buildkit:v0.31.2` (shipped in `toolchain/`).
- SOURCE_DATE_EPOCH: `1795849361` [`SOURCE_DATE_EPOCH.txt`]
- Frozen inputs: [`docs/provenance/FREEZE_MANIFEST.json`], build recipe: [`docs/provenance/BUILD_RECIPE.json`].

## Output

- Published image: `readystack/authentik:2026.8.7-CE-ubuntu24.04-r1` — index digest `sha256:9e4032258290727fd2085fb38bf70ec9a267b2dd714e886a8c2053714c01c538` [`docs/provenance/LOCKED_DIGEST.txt`]
- linux/amd64 image digest `sha256:d7139aa54b1a0860b8767db21a4e3e047ba83a28ca268e30770b900f6f76465f` — reproduced from this archive before publishing [`docs/provenance/REPRO_VERIFICATION.json`].

## Attestations and signature

- SBOM + SLSA provenance attached to the image: attached: an SPDX SBOM and SLSA v1 provenance [`docs/provenance/SCOUT_VERDICT.json`]
- cosign signature by the ReadyStack release key: verified before publishing. Check it: `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/authentik:2026.8.7-CE-ubuntu24.04-r1`

## Pinned inputs, and why

- 26 pinned inputs, each with where it came from, why this one, how it was checked and when it was decided: `docs/PINS.md` [`docs/provenance/PINS.json`] (upstream source 2, base and build images 1, image digests 2, language runtimes and toolchains 1, files the vendor stage downloads 1, pins in the kit's dockerfiles 14, readystack's build engine 1, dependencies upstream chose 2, services the release checks run beside 2).

## Build trail

- How this release passed through the ReadyStack harness, record by record (every chain, drive, stage, review round, defect and check, each naming the record it is copied from): `ReadyStack-authentik-2026.8.7-CE-ubuntu24.04-r1.trail.json`, published beside this archive and signed with the release key (`ReadyStack-authentik-2026.8.7-CE-ubuntu24.04-r1.trail.json.sigstore`), and readable at https://readystack.dev/products/authentik/trail/2026.8.7-CE-ubuntu24.04-r1.

