# Contributions to this Project

## Contributions Welcome

Contributions to this project are always welcome, no matter how large or small. However, all contributing must follow the project's guidelines, conventions, and workflow.

## General Rules

This project follows the [ITS Open-Source Process](https://ite-org.github.io/NTCIP-8008/) and was developed under funding provided by the US DOT.

By providing a contribution to this project, contributors agree to submit their materials according to project's [license](LICENSE.md).

## Pull requests and VERSION

All changes go through pull requests from a **fork**. Every PR must set the root [`VERSION`](VERSION) file.

The `validate-version` check compares your PR's `VERSION` to **`RELEASES` on the upstream base branch** (not whatever happens to be on your fork). You do **not** need a perfect local sync of `RELEASES` for the check to make sense.

### Set VERSION

```bash
# see what upstream already released, then set VERSION to the suggestion
python3 scripts/versioning.py suggest --releases RELEASES
```

Ontology change (must be greater than the latest SemVer on upstream `RELEASES`):

```text
version: 1.2.3-alpha.1
```

Documentation-only (SemVer unchanged; add a date):

```text
version: 1.2.3
doc-only: 2026-07-27
```

### Keep your fork clean

Release automation runs **only on the canonical repo** (`ISO-TC204/ontology-its-core-v1`), not on forks. Still, prefer:

1. Branch from latest upstream `main`
2. Make your edits + one `VERSION` bump
3. Open the PR (GitHub **Squash and merge** is recommended so one commit lands upstream)

If your fork `main` has drifted (extra `chore(release):` bot commits, VERSION ahead of upstream):

```bash
git fetch https://github.com/ISO-TC204/ontology-its-core-v1.git main:upstream-main
git checkout main
git reset --hard upstream-main
git push --force-with-lease origin main
```

Then create a fresh feature branch for new work.

### Maintainer setup

1. Protect `main` and require status check **`validate-version`**.
2. Prefer **Squash and merge** only for PRs into `main`.
