# Changelog

All notable changes to the DevOps Operating Model (named Open Kitchen until 2.0.0) are documented here. Versions follow the [versioning policy](CONTRIBUTING.md#versioning).

## [Unreleased]

### Added

- Images convention: registry paths mirror repository paths, upstream images keep their path behind a proxy cache, tools are tagged by release version and apps by commit SHA, tags never move, manifests and `FROM` lines reference images by tag and digest, any base OS is allowed, and images never run as root.

### Changed

- The manifesto's beliefs are now principles: the manifesto states them in short, and each one links to its section in `1-values/principles.md`, which explains it. Every "belief N" citation across the layers is now "principle N".
- The manifesto and principles no longer say whose they are or where they came from; they stand on their own.
- Releases are cut by pushing an annotated `vX.Y.Z` tag instead of by a version heading reaching `main`. The release is titled `vX.Y.Z — <tag message>`, fails if the changelog section or `CITATION.cff` doesn't match the tag, and can be rerun for an existing tag. `4-practices/releasing.md` describes the new steps.
- The docs checks also run on pull requests and by hand. The link check installs a pinned, checksum-verified lychee with retries instead of using lychee-action, whose single download attempt failed whenever GitHub's release downloads did.

### Removed

- Container images from the FAQ's open challenges.

## [2.0.0] - 2026-11-08

The repository grows from a team model into a whole operating model: values, team, conventions and practices, in four layers that link to each other.

### Added

- Four layers, read in order: `1-values/` (why), `2-team/` (who), `3-conventions/` (what) and `4-practices/` (how). The README explains how they connect.
- Conventions: concerns (the spine shared by groups and repositories), naming (general rules, repositories, clusters and environments), Kubernetes (namespaces, components, objects, labels, field order) and Argo CD. Each convention cites the belief it comes from.
- Practices: placing a tool (including growing a new concern out of `others`), replacing a cluster, releasing and changing the model.
- The manifesto states the system values (recovery, predictability, efficiency) at the top.
- The team record names the group that owns the team's copy of the model.
- FAQ sections for values and conventions.

### Changed

- Renamed the project from Open Kitchen to DevOps Operating Model, and the repository to `devops-operating-model`.
- Renamed recipes to charters, and `templates/recipe.md` to `templates/charter.md`.
- Moved `standards/MANIFESTO.md` and `standards/PRINCIPLES.md` to `1-values/manifesto.md` and `1-values/principles.md`; the manifesto is now the base of the model, not a sample beside it.
- Moved `MODEL.md` and `MEASURING.md` to `2-team/model.md` and `2-team/measuring.md`. The model's values are now called team values, and its principles list is now "In short", so neither is confused with layer 1.
- `ADOPTING.md` covers all four layers, in order.
- Groups are defined once, by the concerns convention, instead of in a table inside the team model.
- Repositories are named `<team>/<concern>/<tool>`, without the environment. Environments live inside the repository. App repositories sit under `<team>/cicd/apps/<app>`.
- Concerns: Networking covers traffic at any OSI layer, Data covers storing data and keeping it safe, and image distribution and registries belong to CI/CD.
- Principles: the environment is no longer part of a name (principles 8 and 11), and the production environment is spelled `prd` (principle 9).
- Weekly changelog template: items name the environment as `<tool> (<environment>)`.
- Concerns change in only two ways, both in "adding a concern": a new concern grows out of `others`, or a group past the split size splits its concern in two.
- The on-call rules name the emergency wait and emergency change review defaults they use.
- Team record: "Standards" is now "Our copy of the model", and the team-level answers are "Our team decisions", matching the adoption guide.

- Feature-review environments live in `dev` as namespaces named `<name>-<branch>`, the one exception to one cluster per environment (principle 11, naming, Kubernetes, Argo CD).

### Removed

- The `owner` namespace label: the `group` label already names the concern, and each concern has one owning group.

## [1.0.2] - 2026-10-28

### Added

- Ranked values replace the goals: reliability, happiness, action, distribution, low maintenance. The higher one wins a collision.
- Rotation cohorts: engineers rotate in different months, and moves balance inside each cohort.
- Rotation rankings: engineers rank the groups they'd like to join.
- Handover window and newcomer on-call wait.
- Borrowing: a short-handed group can borrow an engineer for up to 4 weeks with both gateways' agreement.
- Work spanning several groups is owned by whoever starts it.
- People section: changelog items name who did them, a paragraph per engineer leaving a group, and a monthly one-question team pulse.
- Minimum turnout for votes; only people a group's work affects vote.
- Templates: objection field in change requests, cohorts in the team record, handover in the recipe, SLOs, turnout, pulse and borrowing in the weekly summary.

### Changed

- Core rule: sustained unreliability (missed SLOs or a repeated incident) now forces a review, like sustained unhappiness.
- Between groups: the owning group decides change requests within 3 working days, and no answer means agreed. The team vote is removed.
- Recipes are renewed once a year instead of every rotation.
- No rotation happens during a change freeze.
- Releases are cut from this file: renaming `[Unreleased]` to `[X.Y.Z] - YYYY-MM-DD` and pushing to main runs the docs checks, then tags `vX.Y.Z` and creates the GitHub release with that section as notes.
- Docs checks run only on pushes to main, not on pull requests.
- Renamed counters to groups.
- Renamed charters to recipes, and `templates/charter.md` to `templates/recipe.md`.

## [1.0.1] - 2026-10-11

Plain language. No change in behavior.

### Changed

- Dropped the kitchen metaphor everywhere except the name and the counters: the brigade is now the DevOps team, chefs are engineers, regulars are partners, the family meal is internal work, the test kitchen is R&D, and house standards are standards.
- Removed the kitchen-to-model mapping table and the kitchen column from the concerns table.
- Renamed `templates/brigade.md` to `templates/team.md` (the team record) and `house-standards/` to `standards/`.
- Shortened all docs.

## [1.0.0] - 2026-10-11

First public version.

### Added

- The model: the tech organization as one kitchen, product teams cooking the dishes, and the DevOps team as the brigade running the counters every dish passes through; scope, goal, principles, counters and concerns, chefs and rotation, regulars, Rules 1–4, between counters, on-call, emergency changes, change freezes, the manager.
- Who the counters work for: every dish, and the brigade itself through the family meal.
- House standards and the test kitchen: every kitchen names its manifesto, every counter keeps its standards gap visible, and R&D works to close it.
- Scaling: how chefs spread across counters in small, medium and large brigades, when a crowded counter splits, and how a short-handed counter gets chefs.
- Core rules and defaults, separated so brigades know what they may tune.
- Measuring value: brigade health, DORA delivery metrics and business value in four currencies, a reporting rhythm for the manager and peers, and how the model pairs with the adidas DevOps Maturity Framework and the CNCF Platform Engineering Maturity Model.
- Adoption guide: team-level questions, charter questions with suggested answers, rollout plan.
- Questions and open challenges.
- Sample house standards: the author's DevOps manifesto (17 beliefs) and principles.
- Templates: brigade record, counter charter, weekly changelog, weekly manager summary, monthly value report, change request.

[2.0.0]: https://github.com/hatam-abolghasemi/devops-operating-model/releases/tag/v2.0.0
[1.0.2]: https://github.com/hatam-abolghasemi/devops-operating-model/releases/tag/v1.0.2
[1.0.1]: https://github.com/hatam-abolghasemi/devops-operating-model/releases/tag/v1.0.1
[1.0.0]: https://github.com/hatam-abolghasemi/devops-operating-model/releases/tag/v1.0.0
