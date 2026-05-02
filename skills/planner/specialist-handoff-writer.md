---
name: specialist-handoff-writer
description: Use when the agent needs to turn a Jira ticket, planning result, or review request into a concise, execution-ready handoff for forgeops-builder, forgeops-validator, or forgeops-troubleshooter with the right context, constraints, and exact next objective.
---

# Specialist Handoff Writer

## Overview

Use this skill when the next useful step belongs to another ForgeOps specialist and the planner needs to package context cleanly instead of passing along raw ticket text or bloated notes.

This skill is for handoff preparation and context compression. It does not perform the downstream specialist's work.

## Inputs

Gather whatever is available from the current run:

- Jira ticket or task summary
- current delivery brief or planning result
- relevant acceptance criteria
- known affected repositories, files, services, or environments
- relevant Confluence guidance or repo context
- known assumptions, risks, blockers, or unanswered questions
- any diff summary, review artifact, alert context, or runtime symptom when applicable

Use Atlassian Rovo when Jira or Confluence context is needed to confirm task scope, standards, or architecture.
Use GitHub when repo context or file references help produce a more precise handoff.

## Specialist Targets

### forgeops-builder

Use this target when the next step is implementation work such as drafting Terraform, Ansible, CI, or repository changes.

Include:

- task summary
- requested outcome
- affected repositories and likely paths
- relevant acceptance criteria
- assumptions to preserve
- relevant Confluence or repo context snippets
- known constraints, risks, and open questions
- exact implementation objective for this pass

### forgeops-validator

Use this target when the next step is independent review of a plan, diff, proposed change set, or test evidence.

Include:

- original task goal
- implementation plan or change summary
- affected repositories or files
- acceptance criteria
- review focus areas such as policy, risk, rollback gaps, drift, or missing coverage
- assumptions that should be challenged
- exact validation question or review objective

### forgeops-troubleshooter

Use this target when the next step depends on runtime investigation, drift analysis, logs, metrics, alarms, deployment status, or operational diagnosis.

Include:

- suspected issue or observed symptom
- relevant environment and service context
- recent change context if known
- links to the triggering ticket, alert, incident, or deployment concern when available
- operational question to answer next
- safety constraints or blast-radius concerns already identified

## Workflow

1. Decide which specialist should receive the handoff next.
2. Compress the source material into only the context that changes the downstream agent's work.
3. Keep the original task goal explicit.
4. Preserve acceptance criteria, repo scope, environment assumptions, and risk notes when they matter to the specialist.
5. Remove duplicated background, low-value narrative, and context the specialist does not need.
6. State the exact next objective as a concrete question or task for that specialist.
7. If critical information is missing, name the gap instead of hiding it inside the handoff.
8. Return a concise specialist-ready package.

## Output Contract

Return a concise result with these sections:

- Target specialist
- Task summary
- Required context
- Constraints and assumptions
- Risks or blockers
- Exact next objective

Add one optional section only when it materially helps:

- Review focus
- Runtime signals to inspect
- Likely repo paths

## Quality Bar

A strong handoff should:

- make it obvious why this specialist is the right next step
- carry forward the task goal without forcing the next agent to reread the whole ticket
- preserve only the context that changes downstream decisions
- keep assumptions and risks visible
- end with a single clear next objective
- stay short enough to reduce token waste

## Failure and Ambiguity Handling

- Do not hide missing information behind a polished handoff.
- If the specialist choice is still uncertain, say which two specialists are plausible and what missing detail would resolve the choice.
- If the handoff would be mostly raw pasted context, compress it further before returning it.
- If the request is still too vague for a meaningful handoff, recommend the smallest clarification or planning step first.
