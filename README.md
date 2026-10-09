# vSphere CLI Bundle

PastureStack is an independent community effort to preserve, audit, and modernize the Rancher 1.6 ecosystem. It is not affiliated with or endorsed by Rancher Labs or SUSE.

This repository contains an independent, deterministic packaging recipe for the `govc` command consumed by the PastureStack server compatibility layer. It does not copy the govmomi source tree. The recipe fetches one exact upstream commit, verifies the upstream license, builds with one exact Go toolchain, injects the upstream release metadata, and creates a flat release asset suitable for the central `PastureStack/server` release.

## Release asset

The current recipe produces:

```text
vsphere-cli-bundle-0.55.3-linux-amd64.tar.xz
```

The archive contains:

```text
govc
vsphere-cli-bundle-LICENSES.txt
vsphere-cli-bundle-SOURCES.txt
vsphere-cli-bundle-THIRD-PARTY-NOTICES.txt
```

Run `scripts/test` in an Ubuntu environment with Git, GNU tar, xz, and Go 1.27.2. The test performs two independent builds, compares the archives byte for byte, verifies the fixed source and license, checks the executable format and build metadata, and exercises the compatibility command surface.

Every current and future PastureStack publication uses a pure numeric version, while product identity and provenance remain in package metadata rather than the version string. Earlier publications remain immutable historical evidence.

The package preserves the exact govmomi source commit and uses Go 1.27.2. Its dependency-only override updates `golang.org/x/text` from `v0.39.0` to `v0.41.0` for [GO-2026-6629](https://pkg.go.dev/vuln/GO-2026-6629), changing only `govc/go.mod` and the verified official `govc/go.sum` entries; upstream Go source remains unchanged. The current recipe produces pure numeric version `0.55.3`. It is an unpublished recipe candidate; package publication is a separate reviewed step.

## Distribution model

The public source remains at its authoritative upstream GitHub repository. PastureStack publishes the reviewed bundle as a versioned GitHub Release asset and consumes that immutable asset from the central `PastureStack/server` build. Users do not need to operate an artifact mirror, registry, or additional download service.

## Legal boundary

The root MIT license covers only the PastureStack packaging recipe and documentation. The bundled executable is derived from `vmware/govmomi` and remains governed by its Apache-2.0 license. The archive carries the complete license text and immutable source coordinates. PastureStack does not claim authorship of the upstream project.

See [ORIGIN.md](ORIGIN.md) for exact attribution and [sources.lock.env](sources.lock.env) for immutable build inputs.

## Current release gate

This dependency-only release checks reproducible packaging, the unchanged upstream Go source, the fixed module and the existing offline CLI contracts. It does not claim a new live vSphere lifecycle test. Existing integration evidence is carried only for unchanged paths; live operations not exercised in this release remain explicitly untested. The assembled Server's artifact gate must confirm the fixed dependency.
