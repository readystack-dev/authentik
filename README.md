# authentik: ReadyStack build kit

The offline build kit for the Docker image `readystack/authentik:2026.8.5-CE-ubuntu24.04-r7`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [2026.8.5-CE-ubuntu24.04-r7](https://github.com/readystack-dev/authentik/releases/tag/2026.8.5-CE-ubuntu24.04-r7)
- Image: [`docker.io/readystack/authentik:2026.8.5-CE-ubuntu24.04-r7`](https://hub.docker.com/r/readystack/authentik/tags), manifest digest `sha256:7741676306560bd8e052d1b9468872376109a691d582d4534b39ef1d7fcae8e7`
- Product page: https://readystack.dev/products/authentik
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=authentik

authentik is distributed under its upstream licence (MIT); the kit contains upstream's source under that licence, and each vendored component under its own.

## Download

From the [2026.8.5-CE-ubuntu24.04-r7 release](https://github.com/readystack-dev/authentik/releases/tag/2026.8.5-CE-ubuntu24.04-r7): `ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r7.tar.gz` (645.0 MB), SHA-256 `589f574b3bcd87550845aab0ae2b114785d5ec2d31bd694ec502078a6fb66a57`.

```sh
sha256sum --check --ignore-missing SHA256SUMS
```

## Verify and rebuild

The rebuild statement is signed with the ReadyStack release key. Check the signature before you rely on it:

```sh
cosign verify-blob --key https://readystack.dev/keys/cosign.pub \
  --bundle ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r7.rebuild.json.sigstore ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r7.rebuild.json
```

Unpack with `-p` so file modes are kept, then follow the kit's own README.md and docs/REBUILD.md:

```sh
tar -xpzf ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r7.tar.gz
cd 2026.8.5-CE-ubuntu24.04-r7
less README.md docs/REBUILD.md
```

The build trail (`ReadyStack-authentik-2026.8.5-CE-ubuntu24.04-r7.trail.json`, signed the same way, and its Markdown copy) records how this release was built and checked.

## This repository

`recipe/` holds the kit's recipe files (Dockerfiles, build scripts, pins) as published at https://readystack.dev/products/authentik/recipe. The complete kit is the release download. Each release is a tag here.
