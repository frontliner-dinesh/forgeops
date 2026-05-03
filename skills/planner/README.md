# Planner Skills

Planner skills support `forgeops-planner`, the first active ForgeOps agent in the ForgeOps system.

## Current Skills

- [ticket-to-plan](ticket-to-plan.md): convert a Jira ticket or infrastructure request into an execution-ready delivery plan.
- [repo-selector](repo-selector.md): decide which ForgeOps repository or repositories should own a task and explain the repo-targeting logic.
- [acceptance-criteria-checker](acceptance-criteria-checker.md): determine whether a task is implementation-ready, planning-ready, or still needs clarification.
- [specialist-handoff-writer](specialist-handoff-writer.md): compress planning context into a concise handoff for forgeops-builder, forgeops-validator, or forgeops-troubleshooter.

## Notes

These skills are intentionally focused on planning quality, repo targeting, readiness checks, and downstream handoff preparation.

Deferred planner skills should stay in backlog/docs until the end-to-end ForgeOps workflow has been tested with stronger real cases.
