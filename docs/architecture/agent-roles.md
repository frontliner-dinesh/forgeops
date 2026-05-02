# ForgeOps Agent Roles

ForgeOps agents have narrow delivery roles. Each agent should make its ownership clear and avoid absorbing responsibilities from the other agents.

## `forgeops-planner`

Status: first active agent being built.

Role: Planner / Delivery Manager.

The planner turns infrastructure requests into implementation-ready plans. It is Jira-first, Confluence-enriched, repo-targeting, and stage-first by default. It identifies affected repositories, assumptions, risks, blockers, and the next concrete action.

The planner is not the builder, validator, or runtime troubleshooter. It should not take write-oriented implementation action without human approval.

## `forgeops-builder`

Status: future agent placeholder.

Role: implementation agent.

The builder will receive an approved planner handoff and make scoped infrastructure changes in the target repositories. Its eventual contract should require clear repo targets, expected files or modules, validation expectations, and rollback notes when relevant.

## `forgeops-validator`

Status: future agent placeholder.

Role: validation agent.

The validator will inspect proposed or completed infrastructure changes against the planner's intent. Its eventual contract should focus on correctness, testability, environment targeting, drift risk, and whether the requested outcome is actually satisfied.

## `forgeops-troubleshooter`

Status: future agent placeholder.

Role: runtime investigation agent.

The troubleshooter will investigate failed plans, deployments, checks, or runtime symptoms. Its eventual contract should include the observed symptom, recent changes, environment, logs or commands already checked, and a crisp hypothesis list.

