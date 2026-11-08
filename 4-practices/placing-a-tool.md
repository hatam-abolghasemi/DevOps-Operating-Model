# Placing a tool

*Layer 4 of the [DevOps Operating Model](../README.md): how.*

How a tool gets its one home. It carries out the [concerns](../3-conventions/concerns.md) convention and the team rule that every repository and tool belongs to exactly one [group](../2-team/model.md#groups).

## Before placing

The tool has earned its way in: it solves a real, current problem ([principle 13](../1-values/principles.md#13-solve-real-current-vital-problems)), and the requirement chose it, not the other way around ([principle 14](../1-values/principles.md#14-requirements-choose-tools-not-the-other-way-around)).

## Steps

1. **Ask the removal question.** If this tool were removed, would the need disappear, or only be served worse? Either way, the need that survives is the concern.
2. **Match the need** against the needs in the [concerns table](../3-conventions/concerns.md#the-concerns). Look at the need, not at the tool's category or how it is deployed.
3. **Place it.** Create `<team>/<concern>/<tool>`, named as in [naming](../3-conventions/naming.md#repositories). The concern's group now owns it.
4. **No concern fits?** Place it in `others`. Never invent a one-tool concern.

## Adding a concern

A new concern appears in one of two ways:

- **It grows out of `others`:** several tools there share the same underlying need.
- **A crowded group splits:** a group passes the group split size ([defaults](../2-team/model.md#defaults)), and its concern is split into two needs that each pass the removal question on their own.

Either way:

1. The need is named in one or two words, and added to the [concerns table](../3-conventions/concerns.md#the-concerns) with its definition.
2. The repositories move to `<team>/<new-concern>/`, and their namespaces' `group` label changes with them, following a migration plan ([naming](../3-conventions/naming.md#general)).
3. The team opens a new group for it at the next rotation point ([scaling](../2-team/model.md#scaling)).
4. The change is recorded as described in [changing the model](changing-the-model.md).

Tools never wait in `others` forever: each re-check ([principle 17](../1-values/principles.md#17-nothing-is-frozen-this-repo-included)) asks whether a new concern has formed there.
