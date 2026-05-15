# forgeops-validator starter prompts

## Review plan or handoff
Review this ForgeOps plan or specialist handoff against the requested outcome, acceptance criteria, environment scope, assumptions, risks, rollback notes, and validation expectations. Distinguish confirmed evidence from assumptions and unknowns, then return a clear review outcome with required fixes and the recommended next step.

## Review diff or pull request
Review this diff, pull request, or proposed change set for acceptance-criteria coverage, operational risk, rollback gaps, policy concerns, drift risk, and missing validation evidence. Do not imply deployment success, runtime health, or acceptance-criteria completion without grounded evidence.

## Review rollout or rollback plan
Review this rollout or rollback plan for safety, reversibility, environment scope, evidence gaps, and operational risk. Prefer stage-first recommendations when environment or runtime evidence is unclear, and identify the smallest reviewable fixes needed before approval.

## Validate Jira acceptance criteria
Review this Jira ticket's acceptance criteria against the provided builder output, pull request, diff, or handoff material. Mark each criterion as satisfied, partially covered, unsupported, or missed. If the Jira ticket content or acceptance criteria are not provided, ask for the relevant Jira content instead of assuming it.

## Validate AWS infrastructure standard
Review the provided Terraform, AWS CLI output, inventory export, screenshot, or pasted current-state evidence against this explicit AWS infrastructure standard, such as all launch templates using golden AMI `ami-xxxx`. Do not claim compliance if current-state evidence is missing; instead provide a validation prompt or checklist to gather the missing evidence.

## Prepare ForgeOps repo sync prompt
Prepare a repo-ready Codex prompt to update the ForgeOps repo artifacts so they match approved validator behavior. Include repo URL, branch, files to update, exact behavior or content to sync, commit message, instruction to push to origin main, and the expected commit hash and summary output.
