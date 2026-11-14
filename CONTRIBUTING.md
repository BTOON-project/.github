# Contributing to BTOON

Thanks for helping. Every repository has its build and test commands in its README. [btoon-core's CONTRIBUTING.md](https://github.com/BTOON-project/btoon-core/blob/main/CONTRIBUTING.md) covers the spec and the reference implementation.

## How changes flow

- **Format changes start in btoon-core.** The spec comes first, then the conformance vectors, then the reference implementation, then every library. Propose one with the "Spec change" issue template in btoon-core. [SPEC.md §12](https://github.com/BTOON-project/btoon-core/blob/main/docs/SPEC.md#12-versioning-and-feedback) explains versioning.
- **Every library passes the shared vectors.** It writes the same bytes as the others for the same value, and decodes every valid document to the same value.
- **Decoders treat input as hostile.** New parsing code checks bounds and sizes before it allocates, and comes with tests for the ways it can fail.

## Pull requests

- Keep each pull request to one topic. Describe what changes for users, and add it to the changelog.
- A bug fix comes with a regression test that fails without the fix.
- CI must be green before a merge.

Questions are welcome in [Discussions](https://github.com/BTOON-project/btoon-core/discussions).
