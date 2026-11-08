# Team model

*Layer 2 of the [DevOps Operating Model](../README.md): who.*

How a DevOps team organizes itself so it doesn't split into fixed sub-teams and rebuild the silos DevOps exists to break. The team is organized around technical [concerns](../3-conventions/concerns.md). Each concern has one **group** of engineers. Every engineer is in several groups, and membership rotates, so no group becomes a silo. Each group writes its own **charter**, publishes its work weekly, and is judged by everyone it affects.

## Scope

The model governs the DevOps team only. Other teams organize themselves their own way.

## Team values

In this order. When two collide, the higher one wins. They judge how people organize; the [system values](../1-values/manifesto.md#system-values) judge the systems they run, and the first team value is keeping them.

1. **Reliability.** The system stays up. A happy or fast group that is unreliable is failing.
2. **Happiness.** The team and the people it works with are happy. Load, on-call and dull work are shared fairly, and nobody burns out to keep things running.
3. **Action.** Decisions are made by agreed rules and by the owner, not by politics or endless voting. If you start it or touch it, you own the result.
4. **Distribution.** Knowledge and load spread across the team. No silos, no single person anything depends on.
5. **Low maintenance.** The model runs itself. It asks little of the manager and HR, and little upkeep of the team.

## In short

1. Production comes first. No rule may block operations.
2. Every repository and tool belongs to exactly one group.
3. Each group writes its own charter.
4. Outsiders don't dictate to a group; they vote happy or unhappy.
5. Only sustained unhappiness or unreliability forces a group to review its work.
6. Everything is visible.
7. Every group delivers every week.
8. The team invests in its own tooling and R&D, not only in requests.

## Groups

A group handles one [concern](../3-conventions/concerns.md) and owns every tool and repository in it: `<team>/<concern>/*` in [naming](../3-conventions/naming.md#repositories). Engineers belong to the team; group membership rotates.

The groups are the concerns: Networking, Orchestration, CI/CD, Observability, Data, Security and Others. A new tool is placed by [placing a tool](../4-practices/placing-a-tool.md), and a new concern opens a new group.

## Rotation

- Every engineer is in several groups.
- Each rotation, exactly one of each engineer's groups changes. Everyone rotates.
- Engineers are split into **cohorts** that rotate in different months, so no group loses many people at once. Moves balance inside each cohort: whoever leaves a group is replaced by someone from the same cohort.
- Before each rotation, every engineer in the cohort ranks the groups they'd like to join. A published scheme decides who moves where and follows those rankings as far as group sizes allow.
- **Handover** is the group's charter, its standards gap and one walkthrough. The leaving engineer stays reachable for the handover window.
- A newcomer joins the group's on-call only after the newcomer wait.
- New engineers join at their cohort's rotation point.

## Partners

Partners are specialists from other teams who work with a group, such as a DBA with Data. They read changelogs, vote, and are consulted on changes that affect them. They don't write a group's charter.

## Standards and R&D

The team's standards are the [values](../1-values/manifesto.md) and the [conventions](../3-conventions/) it has adopted. Each group keeps a visible list of where its tools fall short of them: its **standards gap**. R&D works to close it. Experiments stay out of production until proven, and every result is published.

## Rule 1: Minimum weekly output

Each group sets a weekly minimum in its charter and delivers it no matter what. It decides what counts.

## Rule 2: Each group writes its own charter

Each group writes a [charter](../templates/charter.md): how it decides, who leads, how work is shared. Nobody outside approves it. It is renewed once a year.

## Rule 3: Weekly changelog, voting and reliability

Each group publishes a [weekly changelog](../templates/weekly-changelog.md). Every item names who did it.

Anyone the group's work affects can vote thumbs up or down: the team, partners, and teams the group serves. Only cast votes count, and a week counts only when it reaches the minimum turnout.

A group is in trouble when, for the trigger period, either:

- unhappiness stays above the threshold, or
- it misses its SLOs or repeats the same incident.

These are counted automatically, not judged by the manager. Then:

1. The group holds an open session.
2. If it continues, the group reviews its workflow and publishes the changes.
3. If it still continues, the rest of the team writes that group's charter until it recovers.

## Rule 4: One gateway per group

Each group has one contact person, permanent or rotating weekly or monthly, never daily. The gateway takes requests, assigns them and closes them. Requests spanning several groups are split and tracked by the gateway that received them.

## Between groups

- **Changing another group's tools** needs a [change request](../templates/change-request.md). The owning group decides within the answer time. No answer means agreed. A declined requester may log an objection, which the owning group must answer at the next rotation point. There is no team vote.
- **Work spanning several groups** is owned end to end by whoever starts it. The other groups support it through their gateways.
- **Borrowing:** a short-handed group may borrow an engineer from another group for up to the borrow limit, if both gateways agree. The manager is not involved.

## On-call and incidents

- Each group publishes a monthly on-call list and spreads shifts evenly.
- Whoever picks up an alert owns the incident and pulls in others as needed.
- Emergency fixes skip the process and appear in the next changelog.
- Outsiders may change a group's tools only during an incident, if its on-call engineer is unreachable. They report it right away, and the group may revert it.

## Change freezes

SRE or the manager can freeze changes before big events. Only incident fixes go to production. No rotation happens during a freeze.

## People

The model keeps the manager and HR out of collecting evidence:

- Changelogs name who did each item, so each engineer's record builds itself.
- When an engineer leaves a group, the group writes one paragraph about their work there.
- Every month, each engineer answers one question: "Are you happy in your groups?" Low answers are a signal for the next rotation, not a judgment.

## The manager

Manager decisions are followed; overrides are noted in the changelog. The manager gets a weekly summary and a monthly value report ([measuring](measuring.md)).

## Scaling

| Team size | Groups per engineer | Cohorts | On-call |
| --- | --- | --- | --- |
| Small (2–6) | All | 1 | One shared list |
| Medium (7–20) | 2–3 | 2–3 | Per group or shared |
| Large (20+) | 2–3 | 3 | Per group |

A group with too many engineers splits into two concerns, and a new concern opens a new group ([placing a tool](../4-practices/placing-a-tool.md#growing-a-new-concern)). A short-handed group borrows now and gets more engineers at the next rotation point.

## Core rules

Changing any of these means you're no longer running this model.

- Governs the DevOps team only.
- Values ranked as above.
- One group per concern; one group per tool.
- Each group writes its own charter.
- One group per engineer changes each rotation.
- Only sustained unhappiness or unreliability forces a review.
- Weekly changelog and minimum output.
- One gateway per group.
- Visible standards gap.
- Monthly value report.
- Manager decisions are followed.

## Defaults

Tune these in your [team record](../templates/team.md).

| Default | Value |
| --- | --- |
| Rotation period | 6 months |
| Cohorts | 3, two months apart |
| Handover window | 2 weeks |
| Newcomer on-call wait | 4 weeks |
| Unhappiness threshold | Over 80% thumbs down |
| Minimum turnout | 5 votes a week |
| Trigger period | 3 weeks in a row |
| Answer time for change requests | 3 working days |
| Borrow limit | 4 weeks |
| Emergency wait | 15 minutes |
| Emergency change review | 1 working day |
| Group split size | Over 8 engineers |
