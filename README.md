# Node.js V8 canary

This is an automatically updated **experimental** version of [Node.js][] with
the `lkgr` (last known good revision) of V8.

The daily builds of this repo can be found at [`v8-canary`][].

**Do not use this in production!**

This repository is not owned by `@nodejs/v8`, but they might be able to help
with issues.

This project is bound by a [Code of Conduct][].

## How CI Works

The `canary` branch is automatically updated daily by a [GitHub Actions workflow][] that:

1. **Resets to Node.js main**: The workflow starts with the latest code from [`nodejs/node`][Node.js]
2. **Updates V8 to lkgr**: Uses the `git-node` tool to update V8 to the `lkgr` branch — the Last Known Good Revision from [the V8 project's CI][]
3. **Cherry-picks patches**: Applies any floating patches from the `canary-base` branch (manually maintained branch containing V8 patches and backports that Node.js needs)
4. **Verifies the build**: Compiles the code with `./configure && make` and runs the test suite to ensure everything works
5. **Updates the canary branch**: Force-pushes the result to the `canary` branch

### Key Terms

- **lkgr**: Last Known Good Revision — a V8 branch that always points to a stable revision that passes V8's own CI
- **canary-base**: A manually maintained branch containing V8 patches, backports, and changes that Node.js needs but haven't yet landed in V8's main branch
- **canary**: The result branch containing Node.js main + V8 lkgr + cherry-picked patches

The workflow runs daily at 6 AM UTC and can also be triggered manually. On failure, a Slack notification is sent to the team.

[GitHub Actions workflow]: .github/workflows/update-canary.yml
[the V8 project's CI]: https://chromium.googlesource.com/v8/v8/+log/refs/heads/lkgr

[Code of Conduct]: https://github.com/nodejs/admin/blob/HEAD/CODE_OF_CONDUCT.md
[Node.js]: https://github.com/nodejs/node
[`v8-canary`]: https://nodejs.org/download/v8-canary/
