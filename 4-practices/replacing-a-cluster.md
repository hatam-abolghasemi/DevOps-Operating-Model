# Replacing a cluster

*Layer 4 of the [DevOps Operating Model](../README.md): how.*

How to replace a cluster without breaking [one name, everywhere](../1-values/principles.md#9-one-thing-one-name-everywhere). It carries out the [clusters and environments](../3-conventions/naming.md#clusters-and-environments) convention and the [Argo CD sync](../3-conventions/argocd.md#sync) rules.

The environment's name belongs to whichever cluster serves it. Only the outgoing cluster is ever renamed, and only once.

## Steps

1. **Check the safety net.** Every ApplicationSet that targets the cluster sets `preserveResourcesOnDeletion: true`. Without it, the rename in the next step deletes the workloads.
2. **Rename the outgoing cluster** from `<env>` to `<env>-old`. Its Applications regenerate as `<name>-<env>-old`; the workloads keep running.
3. **Register the new cluster** as `<env>`. Its Applications generate as `<name>-<env>`, with the same names the old cluster used to have.
4. **Migrate** traffic and state, one tool or app at a time. Each move appears in the owning group's [weekly changelog](../templates/weekly-changelog.md).
5. **Delete `<env>-old`** once the migration ends. Old and new never live side by side for good ([principle 15](../1-values/principles.md#15-greater-pain-now-is-better-than-gradual-pain-forever)).

The same idea holds for any live workload: renaming one, or changing its selector, means delete and recreate, so it always comes with a migration plan.
