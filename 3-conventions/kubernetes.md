# Kubernetes

*Layer 3 of the [DevOps Operating Model](../README.md): what.*

Rules for the manifests the team writes. They extend [naming](naming.md) inside a cluster. Upstream Helm charts keep their own object names; these rules cover what we write.

## Namespaces

- Namespace = tool or app name, the same in every cluster.
- A feature-review namespace in `dev` is `<name>-<branch>` ([naming](naming.md#clusters-and-environments)). Everything inside it keeps the names it has everywhere else.

## Components

A component is one workload object: Deployment, StatefulSet, DaemonSet, CronJob, Rollout, and so on.

It is named `[<qualifier>-]<entry>`, where the entry is how work reaches it:

| Work arrives by | Entry |
| --- | --- |
| Requests | `api` (`web` for a UI) |
| A queue | `consumer` |
| A schedule | `cron` |
| Its own loop | `worker` |

- Qualify only to tell apart components that share an entry: `api`, `admin-api`, `cron`, `cleanup-cron`.
- What a component produces doesn't count. With two entry points, name it by the main one.
- Upstream role names stay: `ingester`.
- A dependency running inside the namespace, such as an app's own Redis, is named after the tool: `redis`.
- Generic names (`app`, `main`, `server`, `service`) are not allowed.

## Other objects

| Object belongs to | Name | Example |
| --- | --- | --- |
| One component | The component name, no kind suffix | Deployment `api`, Service `api`, HPA `api` |
| Several components | `<purpose>-<kind>` | `db-secret`, `common-configmap` |

- A SealedSecret has the name of the Secret it produces.
- Container name = component name.
- Port names: `http`, `grpc`, `metrics`.

## Labels and annotations

| Where | Key | Value |
| --- | --- | --- |
| Namespace | label `group` | The repository's parent group: a [concern](concerns.md), or `apps` |
| Namespace | label `domain` | The business domain (apps only) |
| A component and its own objects | label `component` | The component name |
| Every object | annotation `deployed-by` | Mandatory, never modified |

- Selectors use `component` only. Shared objects carry no `component` label.
- Ownership is never labelled. The `group` label already names the concern, and each concern has exactly one owning [group of engineers](../2-team/model.md#groups).
- These are the only labels we write. Tools that expect others are configured to read these instead ([belief 9](../1-values/principles.md#9-one-thing-one-name-everywhere)).

## Field order

`apiVersion`, `kind`, `metadata` (`name`, `namespace`, `labels`, `annotations`), `spec`. `namespace` is always explicit ([belief 6](../1-values/principles.md#6-default-is-not-for-production)).
