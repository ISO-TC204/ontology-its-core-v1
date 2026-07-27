# Contributions to this Project

## Contributions Welcome

Contributions to this project are always welcome, no matter how large or small. However, all contributing must follow the project's guidelines, conventions, and workflow.

## General Rules

This project follows the [ITS Open-Source Process](https://ite-org.github.io/NTCIP-8008/) and was developed under funding provided by the US DOT.

By providing a contribution to this project, contributors agree to submit their materials according to project's [license](LICENSE.md).

## Pull requests and VERSION

All changes go through pull requests (typically from a fork). Every PR must update the root [`VERSION`](VERSION) file so the required `validate-version` check can pass.

### Ontology change

Bump the SemVer (must be **greater than** the latest SemVer in [`RELEASES`](RELEASES)):

```text
version: 1.2.3
```

Pre-releases are allowed:

```text
version: 1.2.3-alpha.1
```

After merge, CI stamps `owl:versionInfo` / `owl:versionIRI` / `owl:priorVersion` / `dcterms:modified` in the TTL files, appends `RELEASES`, and creates a GitHub Release tagged `v1.2.3` (marked as a pre-release when a pre-release label is present).

### Documentation-only change

Keep the SemVer unchanged and add a `doc-only` date that is **≥** the latest date in `RELEASES`:

```text
version: 1.2.3
doc-only: 2026-07-27
```

After merge, CI appends a `doc-only` row to `RELEASES` and creates a GitHub Release tagged `docs-2026-07-27` (or `docs-YYYY-MM-DDTHHMMSSZ` if that date tag already exists). TTL ontology identity is not changed.

### Maintainer setup

In the origin repository, protect `main` and require the status check named **`validate-version`**.
