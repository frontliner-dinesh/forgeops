# ForgeOps Handoff Contracts

Handoff contracts define what one ForgeOps agent must provide before another agent can safely continue the work. These contracts should stay small, explicit, and easy to revise.

## `planner -> builder`

Purpose: convert an approved plan into scoped implementation work.

Required planner output:

- Source ticket or request summary.
- Target environment, with stage as the default unless otherwise approved.
- Affected repositories.
- Proposed implementation sequence.
- Files, modules, or infrastructure areas likely to change.
- Assumptions and open questions.
- Risks and rollback considerations.
- Validation expectations.
- Human approval status for write-oriented implementation action.
- Next concrete action for the builder.

Builder should return:

- Summary of changes made.
- Repositories and files changed.
- Commands run.
- Validation results.
- Deviations from the approved plan.
- Follow-up questions or blockers.

## `planner -> validator`

Purpose: verify whether planned or implemented work satisfies the requested outcome.

Required planner output:

- Source ticket or request summary.
- Intended outcome.
- Target environment.
- Affected repositories.
- Planned implementation approach.
- Acceptance criteria or expected behavior.
- Jira ticket content when acceptance-criteria validation depends on Jira.
- Explicit infrastructure standard when reviewing compliance, such as a required golden AMI.
- Validation evidence such as Terraform, AWS CLI output, inventory exports, screenshots, or pasted current-state evidence.
- Known assumptions, risks, and blockers.
- Specific validation questions.

Validator should return:

- Review target.
- Overall assessment.
- Acceptance-criteria coverage.
- Risks and rollback concerns.
- Missing evidence or weak assumptions.
- Required fixes before approval.
- Recommended next step.

Validator should distinguish confirmed evidence from assumptions and unknowns. It must not imply deployment success, runtime health, acceptance-criteria completion, or AWS compliance without grounded evidence. If Jira content is missing for acceptance-criteria review, request it. If current-state evidence is missing for infrastructure compliance review, provide a validation prompt or checklist instead of claiming compliance. If the request is mainly operational diagnosis rather than review, route the need to `forgeops-troubleshooter`.

## `planner -> troubleshooter`

Purpose: investigate blockers, failures, unclear symptoms, runtime issues, drift signals, rollout regressions, or operational ambiguity discovered during planning or delivery.

Required planner output:

- Source ticket or request summary.
- Environment and system scope.
- Observed symptom or blocker.
- Affected repositories or infrastructure areas.
- Recent changes or likely change sources.
- Known assumptions and excluded explanations.
- Logs, metrics, alarms, commands, runbooks, or evidence already reviewed.
- Questions the troubleshooter should answer.

Troubleshooter should return:

- Observed symptom.
- Likely affected environment or service.
- Evidence reviewed.
- Leading hypotheses.
- Blast-radius assessment.
- Safest next checks.
- Possible remediation paths.
- What remains unconfirmed.

Troubleshooter should distinguish symptoms from causes, rank hypotheses by likelihood, and prefer safe verification steps before remediation. It must not claim root cause is confirmed or remediation worked without evidence. If the request is really change review or diff review, it should route the need to `forgeops-validator`.
