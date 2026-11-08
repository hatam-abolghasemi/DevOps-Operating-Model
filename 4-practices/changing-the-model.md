# Changing the model

*Layer 4 of the [DevOps Operating Model](../README.md): how.*

How a team changes its copy of this model: a principle, a team rule, a convention or a practice. Nothing here is frozen ([principle 17](../1-values/principles.md#17-nothing-is-frozen-this-repo-included)), but every change keeps the layers agreeing with each other.

## Who decides

The team's copy of this repository is a repository like any other, so it belongs to exactly one [group](../2-team/model.md#groups). The team names that group in its [team record](../templates/team.md). Anyone else proposes changes through a [change request](../templates/change-request.md), under the usual [between-groups](../2-team/model.md#between-groups) rules.

[Core rules](../2-team/model.md#core-rules) are the exception: changing one means the team runs its own model, not this one.

## Steps

1. **Follow the links down.** A changed principle may break the conventions and practices that cite it. A changed convention may break the practices that carry it out. Update all of them in the same change.
2. **Follow the links up.** A new convention or practice cites the principle or rule it comes from. If it can't cite one, either a principle is missing or the rule isn't needed.
3. **Keep one name.** A renamed term is renamed in every file, template and label at once ([principle 9](../1-values/principles.md#9-one-thing-one-name-everywhere)).
4. **Record it** in `CHANGELOG.md`, and [release](releasing.md) it.
5. **Set the next re-check.** Every decision carries a date to check it again.

## Re-checks

The owning group reviews the whole model once a year, alongside its [charter](../templates/charter.md). Repeated workarounds or a growing `others` concern are reasons to review sooner.
