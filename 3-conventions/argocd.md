# Argo CD

*Layer 3 of the [DevOps Operating Model](../README.md): what.*

Argo CD is a tool like any other. Its own configuration lives in `<team>/cicd/argocd`. These rules apply [naming](naming.md) to the objects it uses to deploy everything else.

## Objects

| Object | Name | Example |
| --- | --- | --- |
| AppProject | Tools: `<concern>`. Apps: `apps-<domain>` | `observability`, `apps-payments` |
| ApplicationSet | `<name>`, in the file `appsets/<group>/<name>.yaml` | `orders` |
| Application | `<name>-<env>`, or `<name>` for something without an environment | `orders-stg`, `gitlab` |

- One ApplicationSet per repository, generating one Application per environment.

## Sync

- Every ApplicationSet sets `preserveResourcesOnDeletion: true`. Renaming a cluster (`stg` to `stg-old`) regenerates its Applications, and without this setting the workloads are deleted. See [replacing a cluster](../4-practices/replacing-a-cluster.md).
- Every environment, `prd` included, auto-syncs with `selfHeal`. Desired state lives in Git ([belief 5](../1-values/principles.md#5-x-as-git)), and the delivery pipeline is the manual gate.
