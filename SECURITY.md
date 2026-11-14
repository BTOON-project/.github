# Security policy

BTOON decoders are meant to parse untrusted input safely:
- every read is bounds-checked;
- nesting, value counts and decompressed size are limited;
- UTF-8 is validated;
- the decoders are fuzzed.

If you find a way around any of that, or another security problem in a BTOON library, please report it privately.

## Reporting a vulnerability

Use GitHub's private vulnerability reporting: in the affected repository, open **Security → Report a vulnerability**. If you're not sure which library is affected, report it against [btoon-core](https://github.com/BTOON-project/btoon-core/security/advisories/new).

Please don't open a public issue, pull request or discussion about a security problem.

Include what you can:
- the library and its version;
- a minimal input (as hex) or program that shows the problem;
- what happens, such as a crash, hang, memory growth, wrong value or a signature check that passes, and what you expected.

## What to expect

- We aim to acknowledge a report within a week, and we'll keep you informed while we investigate.
- Fixes ship as new releases of every affected library, with a GitHub security advisory. We'll credit you if you'd like.
- We'll agree on a disclosure date with you. By default it's the day the fix is released.

## Supported versions

Security fixes go into the latest release line of each library. Before 1.0, older minor versions don't get backports. Each library's changelog says what changes when you upgrade.

## Scope

In scope:
- input that crashes a decoder, hangs it, or makes it use memory beyond the documented limits;
- HMAC signature checks that can be bypassed;
- wrong values decoded from valid documents;
- memory-safety bugs in the native code: btoon-core, and the Python and Node.js bindings.

Out of scope:
- problems that need the caller to raise a limit above its default;
- reports about the behavior of third-party compression libraries that BTOON already rejects safely.
