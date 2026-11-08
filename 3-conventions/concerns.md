# Concerns

*Layer 3 of the [DevOps Operating Model](../README.md): what.*

A concern is a lasting need the team serves. Concerns are the spine of the model: each concern has exactly one [group](../2-team/model.md#groups) of engineers, and exactly one repository group in [naming](naming.md#repositories). Tools come and go; the need they serve stays, so it is the need, not the tool or mechanism, that organizes the team.

## The concerns

The list is flat: concerns never nest. It changes in only two ways, both described in [adding a concern](../4-practices/placing-a-tool.md#adding-a-concern): a new concern grows out of `others`, or a crowded group splits its concern in two.

| Concern | Need | Covers | Sample tools (not all in use) |
| --- | --- | --- | --- |
| `networking` | Traffic at any OSI layer | Routing, load balancing, proxying, service mesh, DNS | haproxy, envoy, kong, apisix, traefik, nginx, varnish, openresty, caddy, istio, linkerd, cilium, coredns, external-dns, bind, metallb, kube-vip, predixy, twemproxy |
| `orchestration` | Where things run | Cluster provisioning, container runtimes, scheduling, scaling, node and OS management | kubespray, kubeadm, k3s, rke2, cluster-api, karmada, kops, containerd, cri-o, keda, descheduler, cluster-autoscaler, vertical-pod-autoscaler, kured, os-management |
| `cicd` | Building, testing and delivering | Pipelines, artifact storage and distribution, deployment and reconciliation, testing; holds the delivered [apps](naming.md#repositories) | gitlab, gitlab-runner, jenkins, tekton, buildkit, kaniko, harbor, nexus, artifactory, chartmuseum, spegel, dragonfly, argocd, argo-rollouts, flux, flagger, helm, helmfile, kustomize, sonarqube, microcks, k6, pact-broker, litmus, trivy, gitleaks, dependency-track, renovate |
| `observability` | Seeing system health | Metrics, logs, traces, errors, alerting | prometheus, mimir, thanos, victoriametrics, telegraf, pmm, tempo, jaeger, opentelemetry-collector, elasticsearch, loki, fluentbit, fluentd, vector, grafana, kibana, sentry, apm-server, alertmanager, karma |
| `data` | Storing data and keeping it safe | Databases, caches, object and block storage, message queues, backup and restore | ceph, minio, redis, rabbitmq, mqtt, velero, etcd-backup |
| `security` | Secrets, policy, identity | Secret management, admission policy, identity and access, cluster hardening checks | vault, sealedsecrets, keycloak, kyverno, kube-bench, kube-hunter |
| `others` | Nothing fits yet | Tools waiting for enough company to form a concern | rocketchat, jitsi, osrm |

## Placing a tool

Every tool belongs to exactly one concern. To find it, imagine removing the tool: the need that remains is its concern. The full procedure is in [placing a tool](../4-practices/placing-a-tool.md).

## Why concerns

- **They outlive tools.** A team split by tool rebuilds itself every time a tool is replaced. A need like "traffic at any OSI layer" lasts for years ([principle 17](../1-values/manifesto.md)).
- **They overlap least.** A tool has one main need, so it has one home. Splitting by mechanism ("everything containerized", "everything Helm") puts one tool in many places ([principle 7](../1-values/principles.md#7-every-translation-has-a-daily-cost)).
- **One name, everywhere.** The same word names the group of engineers, the repository group and the `group` label on every namespace ([principle 9](../1-values/principles.md#9-one-thing-one-name-everywhere)).
