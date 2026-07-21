# vSphere CLI Bundle

PastureStack is an independent community effort to preserve, audit, and modernize the Rancher 1.6 ecosystem. It is not affiliated with or endorsed by Rancher Labs or SUSE.

This repository contains an independent, deterministic packaging recipe for the `govc` command consumed by the PastureStack server compatibility layer. It does not copy the govmomi source tree. The recipe fetches one exact upstream commit, verifies the upstream license, builds with one exact Go toolchain, injects the upstream release metadata, and creates a flat release asset suitable for the central `PastureStack/server` release.

## Release asset

The expected output is:

```text
vsphere-cli-bundle-0.54.1-linux-amd64.tar.xz
```

The archive contains:

```text
govc
vsphere-cli-bundle-LICENSES.txt
vsphere-cli-bundle-SOURCES.txt
vsphere-cli-bundle-THIRD-PARTY-NOTICES.txt
```

Run `scripts/test` in an Ubuntu environment with Git, GNU tar, xz, and Go 1.26.5. The test performs two independent builds, compares the archives byte for byte, verifies the fixed source and license, checks the executable format and build metadata, and exercises the compatibility command surface.

## Distribution model

The public source remains at its authoritative upstream GitHub repository. PastureStack publishes the reviewed bundle as a versioned asset on the central `PastureStack/server` GitHub Release. Users do not need to operate an artifact mirror, registry, or additional download service.

## Legal boundary

The root MIT license covers only the PastureStack packaging recipe and documentation. The bundled executable is derived from `vmware/govmomi` and remains governed by its Apache-2.0 license. The archive carries the complete license text and immutable source coordinates. PastureStack does not claim authorship of the upstream project.

See [ORIGIN.md](ORIGIN.md) for exact attribution and [sources.lock.env](sources.lock.env) for immutable build inputs.

## Current release gate

Package reproducibility and offline command-surface checks do not prove a live vSphere lifecycle. Authenticated inventory, clone, power, delete, upgrade, rollback, and failure recovery remain required integration gates before production publication.
