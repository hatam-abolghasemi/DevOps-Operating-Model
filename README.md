# DevOps Operating Model

*Values, team model, conventions and practices for running a DevOps team, in one place.*

Most DevOps teams keep their beliefs in people's heads, their team rules in a manager's habits, their naming in a wiki page nobody updates, and their practices in tribal memory. Each piece drifts on its own, and the pieces stop agreeing.

This repository keeps all four together, in layers. Each layer is built on the one before it, and every rule links back to the reason it exists.

| Layer | Answers | Contents |
| --- | --- | --- |
| [1. Values](1-values/) | Why | [Manifesto](1-values/manifesto.md): system values and 17 beliefs. [Principles](1-values/principles.md): why each belief holds and how it shows up in daily work. |
| [2. Team](2-team/) | Who | [Model](2-team/model.md): team values, concern groups, rotation, ownership. [Measuring](2-team/measuring.md): how the team proves its value. |
| [3. Conventions](3-conventions/) | What | [Concerns](3-conventions/concerns.md), [naming](3-conventions/naming.md), [Kubernetes](3-conventions/kubernetes.md), [Argo CD](3-conventions/argocd.md). |
| [4. Practices](4-practices/) | How | [Placing a tool](4-practices/placing-a-tool.md), [replacing a cluster](4-practices/replacing-a-cluster.md), [releasing](4-practices/releasing.md), [changing the model](4-practices/changing-the-model.md). |

[Templates](templates/) are ready to copy. [ADOPTING.md](ADOPTING.md) is the starting point, and [FAQ.md](FAQ.md) answers common questions.

## How the layers connect

- **Concerns are the spine.** One list of technical concerns decides both who owns what (each concern has one group of engineers) and where things live (each concern is one repository group).
- **Conventions come from principles.** Names follow beliefs 8 and 9, and environments follow belief 11. Each convention cites its source.
- **Practices carry out conventions and team rules.** Each practice links to what it implements.

## Two value ladders

The repository has two ranked lists of values, because it judges two different things:

- **System values** ([manifesto](1-values/manifesto.md)): recovery, predictability, efficiency. They decide how systems are built and run.
- **Team values** ([model](2-team/model.md)): reliability, happiness, action, distribution, low maintenance. They decide how people organize around those systems.

The ladders meet at the top of the team ladder. Reliability, the team's first value, means keeping the system values.

## License

Docs: [CC BY 4.0](LICENSE). Templates: [CC0 1.0](templates/LICENSE).
