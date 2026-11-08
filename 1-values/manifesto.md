# Manifesto

*Layer 1 of the [DevOps Operating Model](../README.md): why.*

Everything else in this repository is built on these values and principles. Each one links to its section in [principles](principles.md), which explains why it holds and how it shows up in daily work. A team can adopt them as they are, change them, or write its own; the rest of the model still works once the links from the other layers point to the right principle.

## System values

In this order. When two collide, the higher one wins. [Why this order](principles.md#system-values).

1. **Recovery.** How fast we detect, understand and recover from failure.
2. **Predictability.** The system does only what is written down.
3. **Efficiency.** We pay only for what is needed.

## Principles

1. **[Incidents are inevitable. Slow recovery is not.](principles.md#1-incidents-are-inevitable-slow-recovery-is-not)** Post-mortems exist to find ways to minimize MTTR.
2. **[`print` before `return`.](principles.md#2-print-before-return)** Metrics and measurement before production.
3. **[Mistakes are signals, not sins.](principles.md#3-mistakes-are-signals-not-sins)** No incident is `rm -rf /`. Blame hides mistakes, and hidden mistakes repeat.
4. **[Automation speeds up the manual, it doesn't replace it.](principles.md#4-automation-speeds-up-the-manual-it-doesnt-replace-it)** If nobody can do it by hand, the automation is a SPOF.
5. **[X as Git.](principles.md#5-x-as-git)** If it isn't in Git, it didn't happen.
6. **[Default is not for production.](principles.md#6-default-is-not-for-production)** Every value that affects behavior we care about is set on purpose.
7. **[Every translation has a daily cost.](principles.md#7-every-translation-has-a-daily-cost)** Bad names, needless abstractions and variable hells are paid for every day.
8. **[A name is a self-documenting identifier.](principles.md#8-a-name-is-a-self-documenting-identifier)** Not a metadata paragraph.
9. **[One thing, one name, everywhere.](principles.md#9-one-thing-one-name-everywhere)** When forced to rename, rename everywhere. Express different aspects in different views, not in identifiers.
10. **[Failure blast radius decides how much is enough.](principles.md#10-failure-blast-radius-decides-how-much-is-enough)** What breaks, for whom, and at what cost.
11. **[Environments exist to separate the different classes of failure blast radius.](principles.md#11-environments-exist-to-separate-the-different-classes-of-failure-blast-radius)** Each one must name the failure it keeps away from production.
12. **[Idle is waste.](principles.md#12-idle-is-waste)** Slow startup is a bug to fix, not a reason to stay warm.
13. **[Solve real current vital problems.](principles.md#13-solve-real-current-vital-problems)** A flaw that exists today is current, even if its failure hasn't happened yet; a problem a new tool invents is not.
14. **[Requirements choose tools, not the other way around.](principles.md#14-requirements-choose-tools-not-the-other-way-around)** Need a small slice of a big tool? Build it, cleanly. Need most of a flawed tool? Keep it.
15. **[Greater pain now is better than gradual pain forever.](principles.md#15-greater-pain-now-is-better-than-gradual-pain-forever)** Don't carry corpses around: burn them to the ground or bring them back to life.
16. **[Marketing brings the users. Tech keeps them.](principles.md#16-marketing-brings-the-users-tech-keeps-them)** Every decision ends in money, time, risk or customer experience, and every action translates into business metrics.
17. **[Nothing is frozen, this repo included.](principles.md#17-nothing-is-frozen-this-repo-included)** Every decision carries a date to check it again.
