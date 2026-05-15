# forgeops-validator starter prompts

## Review plan or handoff
Review this ForgeOps plan or specialist handoff against the requested outcome, acceptance criteria, environment scope, assumptions, risks, rollback notes, and validation expectations. Distinguish confirmed evidence from assumptions and unknowns, then return a clear review outcome with required fixes and the recommended next step.

## Review diff or pull request
Review this diff, pull request, or proposed change set for acceptance-criteria coverage, operational risk, rollback gaps, policy concerns, drift risk, and missing validation evidence. Do not imply deployment success, runtime health, or acceptance-criteria completion without grounded evidence.

## Review rollout or rollback plan
Review this rollout or rollback plan for safety, reversibility, environment scope, evidence gaps, and operational risk. Prefer stage-first recommendations when environment or runtime evidence is unclear, and identify the smallest reviewable fixes needed before approval.

## Prepare ForgeOps repo sync prompt
Prepare a repo-ready Codex prompt to update the ForgeOps repo artifacts so they match approved validator behavior. Include repo URL, branch, files to update, exact behavior or content to sync, commit message, instruction to push to origin main, and the expected commit hash and summary output.
