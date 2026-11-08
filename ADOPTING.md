# Adopting

How a team starts running the [DevOps Operating Model](README.md). Fork or copy this repository; your copy becomes the team's own model, owned by one group like any other repository ([changing the model](4-practices/changing-the-model.md)).

## Order

Adopt the layers in order. Each one depends on the one before.

1. **Values.** Read the [manifesto](1-values/manifesto.md). Keep it, change it, or write your own. If you change a belief, follow its links down to the conventions that cite it.
2. **Team.** Answer the team decisions below and fill in the [team record](templates/team.md).
3. **Conventions.** Start with [concerns](3-conventions/concerns.md) and [naming](3-conventions/naming.md); they shape the groups and the repositories. Apply [images](3-conventions/images.md), [Kubernetes](3-conventions/kubernetes.md) and [Argo CD](3-conventions/argocd.md) to new work first, and to existing work as each group closes its standards gap.
4. **Practices.** Use them from day one; they need nothing but the layers above.

## Team decisions

Record these in your [team record](templates/team.md).

1. Which values and conventions do we adopt as they are, and which do we change?
2. Which groups do we open? Usually one per [concern](3-conventions/concerns.md) that has tools today.
3. Which group owns our copy of this model?
4. How many groups per engineer?
5. Which defaults do we change?
6. How are first assignments made, which cohort is each engineer in, and how are rankings collected?
7. Where do people vote, and who counts as affected?
8. Which maturity framework do we use?

## Group decisions

Each group answers these in its [charter](templates/charter.md).

| Question | Suggested answer |
| --- | --- |
| Which engineers and tools? | (required) |
| Minimum weekly output? | (required) |
| Do we have a lead? | No, majority decides |
| Tie-breaker? | This week's gateway |
| What needs a group decision? | Production changes |
| Who is the gateway? | Weekly round-robin |
| Who writes the changelog? | The gateway |
| Response time? | 1 working day |
| On-call list? | Round-robin, monthly |
| Who are our partners? | Name them |

## Rollout

| Phase | Duration |
| --- | --- |
| Decide | 2 weeks |
| Pilot with two groups | 8 weeks |
| Review | 1 week |
| All groups | 6 weeks |

Existing repositories move to `<team>/<concern>/<tool>` as their group takes them over. Renaming anything live follows a migration plan ([naming](3-conventions/naming.md#general)).
