[![ReadyStack](https://readystack.dev/logo.svg)](https://readystack.dev)

**Stable, Open-source Releases, Automated** · [readystack.dev](https://readystack.dev)

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub-readystack%2Fauthentik-2496ED?logo=docker&logoColor=white)](https://hub.docker.com/r/readystack/authentik) [![Docker pulls](https://img.shields.io/docker/pulls/readystack/authentik)](https://hub.docker.com/r/readystack/authentik) [![Grade at release](https://img.shields.io/badge/grade%20at%20release-A%20%2894%25%29-2ea44f)](https://readystack.dev/products/authentik) [![Signed: cosign](https://img.shields.io/badge/signed-cosign-2ea44f)](https://readystack.dev/keys/cosign.pub) ![SBOM: SPDX](https://img.shields.io/badge/SBOM-SPDX-2ea44f) ![Provenance: SLSA v1](https://img.shields.io/badge/provenance-SLSA%20v1-2ea44f) ![Offline rebuild: verified](https://img.shields.io/badge/offline%20rebuild-verified-2ea44f)

# authentik: ReadyStack build kit

The offline build kit for the Docker image `readystack/authentik:2026.8.5-CE-ubuntu24.04-r8`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [2026.8.5-CE-ubuntu24.04-r8](https://github.com/readystack-dev/authentik/releases/tag/2026.8.5-CE-ubuntu24.04-r8)
- Image: [`docker.io/readystack/authentik:2026.8.5-CE-ubuntu24.04-r8`](https://hub.docker.com/r/readystack/authentik/tags), manifest digest `sha256:ca993b4c57f308d8769039d6124cdc0151ad7fa279d2439a009be0b623cd819b`
- Product page: https://readystack.dev/products/authentik
- Source and build recipe: https://readystack.dev/products/authentik/recipe
- Build trail: https://readystack.dev/products/authentik/trail/2026.8.5-CE-ubuntu24.04-r8
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=authentik

## The image

ONE product container (the upstream Rust `authentik` binary runs `ak allinone`: it serves the UI/API on :9000 (HTTPS on :9443) itself, runs the embedded proxy outpost and spawns the gunicorn ASGI app plus Python task workers on a Postgres-backed dramatiq broker) PLUS one required datastore sidecar the customer provides: PostgreSQL. NO REDIS — authentik 2026.5 moved cache/channels/sessions/broker to Postgres. NOT a single self-contained image: Postgres is a hard external dependency.

## Who uses authentik and why

System administrators and security engineers who run single sign-on for self-hosted applications.

authentik is an identity provider: people sign in once and reach every connected application over SAML, OAuth, OpenID Connect, LDAP or RADIUS, and administrators manage users and passwords in one place.

A typical use: A small company runs a wiki, a Git server and a monitoring dashboard, each with its own logins. With authentik in front of them, staff sign in once, administrators manage accounts in one place, and deactivating a departing employee's account in authentik stops them signing in to any connected app.

From the upstream project's own description: https://github.com/goauthentik/authentik, https://docs.goauthentik.io/.

## This release

- Docker Scout policy grade at release: **A** (94%), graded 2026-11-25 with `docker scout policy` (CLI 1.26.0, docker-default configuration).
  - Docker Scout counts 114 packages with copyleft licences (GPL, LGPL, MPL), 108 of them operating-system packages (it counts only packages whose licence it can read; the SBOM lists every component).
- Signed with ReadyStack's release key (fingerprint `04daa92344a52dbc`): https://readystack.dev/keys/cosign.pub.
- Runs as a non-root user (`1000`).
- Attestations on the image: an SPDX SBOM and SLSA provenance v1.
- Rebuilt from this kit with network egress blocked on 2026-11-25; the rebuilt image digest is the published one.
- Base: Ubuntu 24.04.

The current grade, measured again every day, is on https://readystack.dev/products/authentik.

authentik is distributed under its upstream licence (MIT); the kit contains upstream's source under that licence, and each vendored component under its own.

## Download

From the [2026.8.5-CE-ubuntu24.04-r8 release](https://github.com/readystack-dev/authentik/releases/tag/2026.8.5-CE-ubuntu24.04-r8): `ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r8.tar.gz` (645.0 MB), SHA-256 `ce53135df3d5afdad5f0d95a002120e2aa46934d32d6775bd0ee9ebcfc1823e8`.

```sh
sha256sum --check --ignore-missing SHA256SUMS
```

## Verify and rebuild

The rebuild statement is signed with the ReadyStack release key. Check the signature before you rely on it:

```sh
cosign verify-blob --key https://readystack.dev/keys/cosign.pub \
  --bundle ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r8.rebuild.json.sigstore ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r8.rebuild.json
```

Unpack with `-p` so file modes are kept, then follow the kit's own README.md and docs/REBUILD.md:

```sh
tar -xpzf ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r8.tar.gz
cd 2026.8.5-CE-ubuntu24.04-r8
less README.md docs/REBUILD.md
```

The build trail (`ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r8.trail.json`, signed the same way, and its Markdown copy) records how this release was built and checked.

## This repository

`recipe/` holds the kit's recipe files (Dockerfiles, build scripts, pins) as published at https://readystack.dev/products/authentik/recipe. The complete kit is the release download. Each release is a tag here. How to report a vulnerability: [SECURITY.md](SECURITY.md).

## About ReadyStack

**Stable, Open-source Releases, Automated.** ReadyStack releases popular open-source apps every week with every available critical and high security fix applied, plus full documentation, reference data, tests and a build recipe that recreates each release bit-for-bit. Each release is rebuilt from its pinned inputs with the network off, checked against its published digest, signed, and scanned and graded again every day. The images and build kits are free, and ReadyStack is soon to be a nonprofit.

[readystack.dev](https://readystack.dev) · [All products](https://readystack.dev/products.html) · [Build kits on GitHub](https://github.com/readystack-dev) · [Defect log](https://readystack.dev/defects.html) · contact@readystack.dev

— ReadyStack · https://readystack.dev
