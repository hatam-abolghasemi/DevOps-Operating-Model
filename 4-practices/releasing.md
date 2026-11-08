# Releasing

*Layer 4 of the [DevOps Operating Model](../README.md): how.*

How the team releases the tools it builds, and this repository itself. The changelog is the release: what is written is what ships ([predictability](../1-values/manifesto.md#system-values)), and every release is in Git ([belief 5](../1-values/principles.md#5-x-as-git)).

## Rules

- Work is committed straight to `main`. No release branches, no merge-based release flow.
- Every change that affects behavior goes into `CHANGELOG.md`, under `## [Unreleased]`, in the same commit as the change.
- Versions follow [Semantic Versioning](https://semver.org/): major when users must change something, minor for something new and optional, patch for fixes and wording.

## Steps

1. Rename `## [Unreleased]` to `## [X.Y.Z] - YYYY-MM-DD`, and add a fresh, empty `## [Unreleased]` above it.
2. Add the version's link at the bottom of the changelog.
3. Bump any other file that states the version, such as `CITATION.cff`.
4. Commit and push to `main`.

The pipeline does the rest. It runs the checks, tags `vX.Y.Z`, and publishes a release with that changelog section as its notes. A push with no new version heading releases nothing. This repository's own pipeline is [release.yml](../.github/workflows/release.yml).
