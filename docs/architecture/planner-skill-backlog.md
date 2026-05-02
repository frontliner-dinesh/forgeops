# Planner Skill Backlog

`forgeops-planner` is intentionally paused after these attached skills:

- `ticket-to-plan`
- `repo-selector`
- `acceptance-criteria-checker`
- `specialist-handoff-writer`

These skills are enough to support the first planner workflow without overbuilding the agent before there is stronger end-to-end evidence.

## Deferred planner skills

### `risk-and-rollback-checker`

- Purpose: review a plan for delivery risk, blast radius, reversibility, and rollback readiness.
- Use when a planned change touches production, security-sensitive infrastructure, shared modules, or hard-to-reverse resources.
- Would help convert generic risk notes into concrete mitigation and rollback expectations.
- Deferred because risk scoring should be calibrated against real ForgeOps planner outputs and builder handoffs.
- Deferred because rollback requirements may vary by repository and environment once actual workflows are tested.

### `context-compressor`

- Purpose: reduce tickets, Confluence notes, repo findings, and discussion history into compact planning context.
- Use when source material is too long for a clean planner response or specialist handoff.
- Would help preserve important facts while removing duplicated background and low-value narrative.
- Deferred because the current attached skills already include basic context compression inside planning and handoff workflows.
- Deferred until there are repeat examples showing what context the planner consistently over-includes or drops.

### `validation-scope-writer`

- Purpose: turn a plan or change summary into a focused validation scope for `forgeops-validator`.
- Use when a builder handoff, implementation plan, or diff needs specific validation questions and evidence expectations.
- Would help separate Terraform, Ansible, environment, rollback, and operational validation concerns.
- Deferred because validation scope should be based on real builder output and validator review patterns.
- Deferred until ForgeOps has a stronger example of what validation evidence is expected per repo and environment.

### `runtime-triage-router`

- Purpose: decide whether a request should stay with the planner or be routed to `forgeops-troubleshooter`.
- Use when a Jira ticket mixes implementation intent with runtime symptoms, alerts, failed deploys, drift, or unclear operational behavior.
- Would help keep `forgeops-planner` from absorbing deep runtime diagnosis.
- Deferred because runtime routing should be tested against real incidents, alerts, logs, and deployment failure examples.
- Deferred until the troubleshooter handoff contract is exercised with actual end-to-end ForgeOps cases.

## Why deferred for now

These planner skills are intentionally postponed until there is a stronger end-to-end workflow test case for ForgeOps.

The current attached skills cover the first useful planner loop: convert intake to a plan, choose target repositories, check readiness, and write specialist handoffs. Adding more skills before that loop is tested would create extra source documents without proving which behaviors need to be separate skills.

The next step is to run ForgeOps through realistic tickets and handoffs, then promote backlog items when repeated workflow gaps are visible.
