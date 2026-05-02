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
- Known assumptions, risks, and blockers.
- Specific validation questions.

Validator should return:

- Pass/fail or blocked status.
- Evidence reviewed.
- Validation commands or checks run.
- Findings with severity.
- Gaps in acceptance criteria.
- Recommended next action.

## `planner -> troubleshooter`

Purpose: investigate blockers, failures, unclear symptoms, or runtime issues discovered during planning or delivery.

Required planner output:

- Source ticket or request summary.
- Environment and system scope.
- Observed symptom or blocker.
- Affected repositories or infrastructure areas.
- Recent changes or likely change sources.
- Known assumptions and excluded explanations.
- Logs, commands, or evidence already reviewed.
- Questions the troubleshooter should answer.

Troubleshooter should return:

- Root cause if known.
- Ranked hypotheses if root cause is not confirmed.
- Evidence gathered.
- Commands or logs reviewed.
- Immediate mitigation options.
- Recommended owner and next concrete action.

