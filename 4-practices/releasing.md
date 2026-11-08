# Releasing

*Layer 4 of the [DevOps Operating Model](../README.md): how.*

How the team releases the tools it builds, and this repository itself. The changelog is the release: what is written is what ships ([predictability](../1-values/manifesto.md#system-values)), and every release is in Git ([principle 5](../1-values/principles.md#5-x-as-git)).

## Rules

- Work is committed straight to `main`. No release branches, no merge-based release flow.
- Every change that affects behavior goes into `CHANGELOG.md`, under `## [Unreleased]`, in the same commit as the change.
- Versions follow [Semantic Versioning](https://semver.org/): major when users must change something, minor for something new and optional, patch for fixes and wording.

## Steps

1. Rename `## [Unreleased]` to `## [X.Y.Z] - YYYY-MM-DD`, and add a fresh, empty `## [Unreleased]` above it.
2. Add the version's link at the bottom of the changelog.
3. Bump any other file that states the version, such as `CITATION.cff`.
4. Commit and push to `main`.
5. Tag that commit with an annotated tag whose message is a short title, and push the tag:

   ```sh
   git tag -a vX.Y.Z -m "short description"
   git push origin vX.Y.Z
   ```

The tag is the release, so a release happens only when someone decides it should; pushing to `main` alone releases nothing. The pipeline checks that the tag, the changelog and every file stating the version agree, runs the checks, and publishes a release titled `vX.Y.Z — <tag message>` with that changelog section as its notes. Rerunning it for an existing tag rewrites that release from the changelog. This repository's own pipeline is [release.yml](../.github/workflows/release.yml).
