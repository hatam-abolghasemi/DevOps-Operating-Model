# FAQ

## Values

**Do we have to adopt these beliefs?**
No. They are one engineer's beliefs, and the rest of the model works with your own. Conventions cite beliefs, so update those links when you change one.

**Why two value ladders?**
They judge different things. System values judge how systems behave; team values judge how people organize. Reliability, the first team value, is where they meet.

## Team

**Does it manage developers or QA?**
No. Only the DevOps team.

**Does it replace Scrum or Kanban?**
No. Each group picks its own workflow.

**Isn't voting a popularity contest?**
It measures happiness on purpose. One bad week changes nothing.

**Doesn't rotation destroy expertise?**
Only one group changes per rotation, and cohorts rotate in different months, so a group loses at most one or two people at a time.

**Why does the owning group decide instead of a team vote?**
Action ranks above democracy. A vote is slow and lets people far from the tool outvote those who run it. The requester's objection is logged and must be answered at the next rotation point.

**Can a well-liked group stay unreliable?**
No. Missed SLOs or a repeated incident start the same review as unhappiness.

**Does a small team need all this?**
Engineers are in every group, so rotation barely applies. The rest still works.

**Is DORA the EU regulation?**
No. DevOps Research and Assessment.

## Conventions

**Why concerns, not tools or business domains?**
Concerns outlive tools and overlap least. A team split by business domain repeats the same tools in every domain, and a team split by tool reorganizes every time a tool is replaced. See [concerns](3-conventions/concerns.md#why-concerns).

**Why no environment in names?**
The environment is where something runs, not what it is ([belief 8](1-values/principles.md#8-a-name-is-a-self-documenting-identifier)). Putting it in the name multiplies repositories and breaks when things move.

**Why are images referenced by digest too?**
A tag is for people and can be moved by mistake; a digest can't. Writing both keeps the manifest readable and what runs exact ([images](3-conventions/images.md#references)).

**Why no owner label?**
Each concern has exactly one owning group, and the `group` label already names the concern. A second label would be a second place to keep in sync.

## Open challenges

- Measuring the value of internal work and prevented incidents.
- Organized voting by a few unhappy teams.
- Mapping to OKRs or sprints.
- How much say partners should have.

Ideas welcome in [Discussions](https://github.com/hatam-abolghasemi/devops-operating-model/discussions).
