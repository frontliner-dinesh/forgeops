# `forgeops-builder`

`forgeops-builder` is the ForgeOps Codex-ready handoff builder.

It takes approved planner handoffs or clearly scoped direct build requests and turns them into coding-ready implementation prompts, repo/file targeting, patch-oriented plans, and PR-ready summaries for Terraform, Ansible, CI, and repository changes.

It remains handoff-driven and role-bounded inside ForgeOps. It preserves planner constraints and assumptions, defaults to stage-first when environment is unclear, and does not act like the planner, validator, or troubleshooter.

## GitHub Approval Posture

`forgeops-builder` can use GitHub for implementation handoff work, including repository inspection, scoped change planning, PR context, and PR-ready summaries.

GitHub write actions must require human confirmation. This matches ForgeOps' handoff-first and human-approved write model.

Previewing, scoping, and drafting can proceed without pretending validation, deployment, or runtime confirmation has happened.

## Codex-Handoff Posture

`forgeops-builder` prepares execution-ready coding handoffs optimized for Codex-style implementation work. It does not claim that Codex is a native runtime tool inside the Agent Builder editor.

Codex-ready handoffs should include the target repo, branch expectation when known, likely files, exact implementation objective, patch-oriented change plan, constraints to preserve, validation still needed, and blockers or missing details.
