# Provenance — authentik (`2026.8.5-CE-ubuntu24.04-r7`)

Every item below is copied from a record in this archive; the record is named in brackets.

## Source

- Upstream repository: https://github.com/goauthentik/authentik
- Revision built: `version/2026.8.5` (commit `4ec0d19b98da3c329781894cd550da95d3033954`)
- Source tree: `45feb928b7089687fe03f0520bba32c23f9be87bf51e33786c55bb954067e01b` over 6120 files [`docs/provenance/SOURCE_TREE_HASH.json`]
- Community Edition only: enterprise code is removed or refused before the build (CE audit at acquire).

## Build

- Method: `source-rebuild-python`; base image `ubuntu:24.04`
- Compiled with `--network=none` from vendored source, dependencies and base images; BuildKit pinned to `moby/buildkit:v0.31.2` (shipped in `toolchain/`).
- SOURCE_DATE_EPOCH: `1795407184` [`SOURCE_DATE_EPOCH.txt`]
- Frozen inputs: [`docs/provenance/FREEZE_MANIFEST.json`], build recipe: [`docs/provenance/BUILD_RECIPE.json`].

## Output

- Published image: `readystack/authentik:2026.8.5-CE-ubuntu24.04-r7` — index digest `sha256:675350e3afa51c114a8ec7d8adcc14c1bb0721aed98136e05861b1aab646b1b3` [`docs/provenance/LOCKED_DIGEST.txt`]
- linux/amd64 image digest `sha256:7741676306560bd8e052d1b9468872376109a691d582d4534b39ef1d7fcae8e7` — reproduced from this archive before publishing [`docs/provenance/REPRO_VERIFICATION.json`].

## Attestations and signature

- SBOM + SLSA provenance attached to the image: attached: an SPDX SBOM and SLSA v1 provenance [`docs/provenance/SCOUT_VERDICT.json`]
- cosign signature by the ReadyStack release key: verified before publishing. Check it: `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/authentik:2026.8.5-CE-ubuntu24.04-r7`

## Pinned inputs, and why

- 26 pinned inputs, each with where it came from, why this one, how it was checked and when it was decided: `docs/PINS.md` [`docs/provenance/PINS.json`] (upstream source 2, base and build images 1, image digests 2, language runtimes and toolchains 1, files the vendor stage downloads 1, pins in the kit's dockerfiles 14, readystack's build engine 1, dependencies upstream chose 2, services the release checks run beside 2).

## Build trail

- How this release passed through the ReadyStack harness, record by record (every chain, drive, stage, review round, defect and check, each naming the record it is copied from): `ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r7.trail.json`, published beside this archive and signed with the release key (`ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r7.trail.json.sigstore`), and readable at https://readystack.dev/products/authentik/trail/2026.8.5-CE-ubuntu24.04-r7.

