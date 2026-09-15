# Node.js V8 canary

This is an automatically updated **experimental** version of [Node.js][] with
the `lkgr` (last known good revision) of V8.

The daily builds of this repo can be found at [`v8-canary`][].

**Do not use this in production!**

## Continuous Integration

This repository uses GitHub Actions to automatically test Node.js with bleeding-edge V8.

### How It Works

**The Canary Branch:** The `canary` branch tracks the V8 canary—the latest commits from V8's development branch. This represents the most recent V8 code, often weeks or months ahead of official V8 releases.

**V8 LKGR (Last Known Good Revision):** The V8 team tags certain commits as "LKGR" when they pass V8's own test suite. These are commits the V8 team considers stable enough for downstream users. This repository automatically tracks V8's LKGR, ensuring we're always testing against a version of V8 that has passed upstream testing.

**The Workflow:** GitHub Actions periodically fetches the latest V8 canary commits and updates the `canary` branch in this repository. Node.js is then built against this V8 version, and the full Node.js test suite runs to catch compatibility issues.

### Why This Matters

- **Early Detection:** By testing against V8's canary, we discover compatibility issues with upcoming V8 changes before they're released to the wider Node.js ecosystem.
- **Upstream Coordination:** This helps Node.js maintainers prepare for and influence incoming V8 changes.
- **Continuous Updates:** The `canary` branch is automatically kept in sync, so the latest V8 code is always being tested against Node.js.

This repository is not owned by `@nodejs/v8`, but they might be able to help
with issues.

This project is bound by a [Code of Conduct][].

[Code of Conduct]: https://github.com/nodejs/admin/blob/HEAD/CODE_OF_CONDUCT.md
[Node.js]: https://github.com/nodejs/node
[`v8-canary`]: https://nodejs.org/download/v8-canary/
