# Naming

*Layer 3 of the [DevOps Operating Model](../README.md): what.*

Naming and placement rules for everything the team runs. They put [belief 8](../1-values/principles.md#8-a-name-is-a-self-documenting-identifier) (a name identifies, it doesn't describe) and [belief 9](../1-values/principles.md#9-one-thing-one-name-everywhere) (one thing, one name, everywhere) into practice. Container images are out of scope for now.

## General

- Names use lowercase letters, digits and `-` only. At most 63 characters.
- A name says what a thing is, never where it runs, who owns it, how it is deployed, or what it replaced. Location, ownership, mechanism and history are metadata: labels, annotations and docs.
- Names are unique across the team's top-level repository group. A repository name is also its namespace name.
- Anything without an environment drops the environment everywhere: `gitlab`, never `gitlab-prd`.
- Never rename a live workload or change its selector without a migration plan. Both mean delete and recreate.

## Repositories

```text
<team>/<concern>/<tool>
<team>/cicd/apps/<app>
```

For example `devops/networking/haproxy` and `devops/cicd/apps/orders`.

- **Concern:** one of the [concerns](concerns.md).
- **Tool:** infrastructure software, upstream or the team's own. Named after the project: `loki`, `haproxy`, `angryduck`.
- **App:** an application the company builds for its business. Its repository holds the desired state the delivery pipeline writes and deploys from ([belief 5](../1-values/principles.md#5-x-as-git)).
- One repository per tool or app. Environments live inside the repository (overlays, inventories), never in its name.
- Each repository belongs to exactly one group: the group of its concern. Apps belong to the CI/CD group.

## Clusters and environments

Environments follow [belief 11](../1-values/principles.md#11-environments-exist-to-separate-the-different-classes-of-failure-blast-radius): each one separates a class of failure from production.

- One cluster per environment; the cluster is the environment.
- Environment names: `prd`, `dr`, `uat`, `stg`, `dev`. These spellings are used everywhere: clusters, labels, dashboards, docs and changelogs.
- A cluster that is not an environment is named after what it hosts.
- Site, datacenter and hardware are labels on the cluster, never part of its name.
- A replaced cluster is renamed once, to `<env>-old`, while the new one takes `<env>`. See [replacing a cluster](../4-practices/replacing-a-cluster.md).
