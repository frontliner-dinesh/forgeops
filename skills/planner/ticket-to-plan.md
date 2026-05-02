---
name: ticket-to-plan
description: Use when the agent needs to convert a Jira ticket or infrastructure request into an execution-ready delivery plan with explicit repo targeting, assumptions, risks, blockers, validation expectations, and a recommended next specialist handoff.
---

# Ticket to Plan

## Overview

Use this skill when the current task is to turn a Jira ticket or infrastructure request into a delivery plan that another specialist or human operator can act on.

This skill is for planning and handoff preparation. It does not perform write-oriented implementation work.

## Inputs

Gather whatever is available from the current run:

- Jira ticket ID or Jira ticket content
- request summary when no ticket is available
- relevant Confluence links or excerpts
- target environment, if specified
- known affected service, module, stack, or repository
- operator constraints, deadlines, or acceptance criteria

Use Atlassian Rovo as the primary source for Jira and Confluence context when that app is available.
Use GitHub to inspect repository structure and existing patterns when repo targeting or implementation approach needs confirmation.

## Workflow

1. Treat the Jira ticket or request as the source of truth for the requested outcome.
2. Identify the target environment. If it is absent or ambiguous, default to stage-first planning and call out that assumption explicitly.
3. Extract the requested outcome, acceptance criteria, constraints, dependencies, deadlines, and definition of done.
4. Enrich with Confluence context when it clarifies architecture, procedures, ownership, standards, or prior decisions.
5. Identify the likely affected repositories:
   - `Forecast-5-Analytics/dna-terraform-modules`
   - `Forecast-5-Analytics/dna-terraform-infrastructure`
   - `Forecast-5-Analytics/dna-ansible-playbooks`
6. Separate confirmed facts from assumptions.
7. Identify risks, blockers, and missing information that materially affect delivery.
8. Draft an implementation-ready plan that is specific enough for a builder, validator, or human operator to continue.
9. Define the validation expectations for the planned work.
10. Recommend the next concrete action and the right next specialist when a handoff is needed.

## Repo Targeting Rules

Use these defaults when choosing where the work belongs:

- Choose `dna-terraform-modules` for reusable Terraform building blocks or shared module logic.
- Choose `dna-terraform-infrastructure` for environment-specific composition, wiring, rollout configuration, or stack instantiation.
- Choose `dna-ansible-playbooks` for host configuration, post-provisioning automation, or operational playbook changes.
- If more than one repo is likely involved, provide a ranked or split recommendation and explain why.

## Output Contract

Return a concise delivery brief with these sections:

- Summary
- Source ticket or request
- Target environment
- Affected repos
- Implementation plan
- Assumptions
- Risks
- Blockers
- Validation expectations
- Handoff recommendation
- Next concrete action

## Quality Bar

A strong output should:

- be specific enough for a builder or human operator to continue without re-reading the full ticket
- make the target environment explicit and default to stage-first when needed
- name the affected repositories instead of implying them
- label assumptions as assumptions
- tie risks to the proposed work rather than listing generic warnings
- give actionable blockers
- define validation expectations clearly enough to execute
- end with a single reviewable next concrete action

## Failure and Ambiguity Handling

- Do not invent missing facts when the ticket or request is incomplete.
- If the target environment is unclear, assume stage for planning purposes and call out that assumption.
- If the affected repository is unclear, provide a ranked repo hypothesis and explain why each repo may be involved.
- If the request appears production-impacting, security-sensitive, or hard to reverse, explicitly mark it as requiring human approval before write-oriented implementation work.
- If runtime symptoms dominate the request, prepare a planner-to-troubleshooter handoff instead of trying to diagnose deeply inside the planning step.
