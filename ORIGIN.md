# Origin and attribution

This repository is an independent packaging project. It is not a fork and does not contain a copy of the upstream source tree.

The packaged `govc` executable is built from:

- Project: `vmware/govmomi`
- Repository: <https://github.com/vmware/govmomi>
- Reference release tag: `v0.55.1`
- Pinned post-release commit: `a668d9c60399552ea96782b8751c956720a0b8fb`
- Security dependency: `golang.org/x/text v0.39.0`
- License: Apache-2.0
- License file: `LICENSE.txt`

The pinned commit is the upstream dependency-maintenance commit published after `v0.55.1` that updates `golang.org/x/text` to its security-fixed version. It is recorded as an exact source coordinate, not represented as a direct descendant of the reference tag. The package suffix makes this boundary explicit. The packaging recipe verifies the exact commit, dependency version, and SHA-256 of the upstream license before building.

The root MIT license applies only to PastureStack-authored packaging code and documentation. The upstream copyright and Apache-2.0 terms remain intact and are reproduced in every release archive.
