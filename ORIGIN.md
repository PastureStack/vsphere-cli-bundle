# Origin and attribution

This repository is an independent packaging project. It is not a fork and does not contain a copy of the upstream source tree.

The packaged `govc` executable is built from:

- Project: `vmware/govmomi`
- Repository: <https://github.com/vmware/govmomi>
- Reference release tag: `v0.55.1`
- Pinned post-release commit: `a668d9c60399552ea96782b8751c956720a0b8fb`
- Base upstream dependency: `golang.org/x/text v0.39.0`
- Packaged security dependency: `golang.org/x/text v0.41.0`
- License: Apache-2.0
- License file: `LICENSE.txt`

The pinned commit is an exact source coordinate, not represented as a direct descendant of the reference tag. The packaging recipe preserves every upstream Go source file and applies only an explicit `govc/go.mod` requirement plus official `govc/go.sum` checksum entries for `golang.org/x/text v0.41.0`, addressing [GO-2026-6629](https://pkg.go.dev/vuln/GO-2026-6629). It verifies the complete two-file change allowlist, exact dependency version and module checksums, and the upstream license SHA-256 before building pure numeric version `0.55.3` with Go 1.27.0.

The root MIT license applies only to PastureStack-authored packaging code and documentation. The upstream copyright and Apache-2.0 terms remain intact and are reproduced in every release archive.
