# authentik: ReadyStack build kit

The offline build kit for the Docker image `readystack/authentik:2026.8.5-CE-ubuntu24.04-r8`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [2026.8.5-CE-ubuntu24.04-r8](https://github.com/readystack-dev/authentik/releases/tag/2026.8.5-CE-ubuntu24.04-r8)
- Image: [`docker.io/readystack/authentik:2026.8.5-CE-ubuntu24.04-r8`](https://hub.docker.com/r/readystack/authentik/tags), manifest digest `sha256:ca993b4c57f308d8769039d6124cdc0151ad7fa279d2439a009be0b623cd819b`
- Product page: https://readystack.dev/products/authentik
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=authentik

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

`recipe/` holds the kit's recipe files (Dockerfiles, build scripts, pins) as published at https://readystack.dev/products/authentik/recipe. The complete kit is the release download. Each release is a tag here.
