---
name: acceptance-criteria-checker
description: Use when the agent needs to judge whether a Jira ticket or infrastructure task is implementation-ready, identify missing or weak acceptance criteria, separate confirmed requirements from assumptions, and recommend the smallest clarification needed before handoff or build work starts.
---

# Acceptance Criteria Checker

## Overview

Use this skill when the current task needs a readiness check before planning is finalized or before work is handed to another specialist.

This skill is for requirement clarity and delivery readiness. It does not perform implementation work.

## Inputs

Gather whatever is available from the current run:

- Jira ticket content or task summary
- explicit acceptance criteria, if any
- linked Confluence notes or design context
- target environment, service, module, or repo context
- known constraints, deadlines, dependencies, or rollout requirements
- any existing implementation plan or handoff draft

Use Atlassian Rovo when Jira or Confluence context is needed to confirm the intended outcome, standards, or missing requirements.
Use GitHub only when repository context helps determine whether the task is specific enough to execute or validate.

## What To Check

Check whether the task clearly defines:

- the requested outcome
- the target environment or rollout expectation
- the affected system, service, repo, module, or playbook area
- what success looks like
- any important constraints, dependencies, or standards
- validation expectations
- whether the task can move to planning, build, validation, or troubleshooting without material guessing

## Workflow

1. Read the task and identify the stated outcome, acceptance criteria, and definition of done.
2. Separate explicit requirements from inferred assumptions.
3. Check whether the requested work is concrete enough to plan or hand off safely.
4. Identify missing criteria that would materially change repo targeting, implementation shape, validation scope, or operational risk.
5. Flag vague phrases such as "update as needed," "fix the issue," or "make it work" when they do not define a reviewable outcome.
6. Determine whether the task is:
   - implementation-ready
   - planning-ready but not implementation-ready
   - not ready and needs clarification first
7. Recommend the smallest useful clarification when more information is needed.
8. Return a concise readiness assessment that the planner can use directly.

## Output Contract

Return a concise result with these sections:

- Task summary
- Explicit acceptance criteria
- Assumptions currently required
- Readiness assessment
- Missing or weak criteria
- Why the gaps matter
- Smallest clarification needed
- Recommended next step

## Readiness Rules

Treat the task as **implementation-ready** only when the requested outcome and success condition are clear enough that a builder would not need to guess about the core change.

Treat the task as **planning-ready** when the planner can still produce a solid delivery brief, but a builder or validator would need clarification before execution.

Treat the task as **not ready** when key details such as target environment, affected area, expected result, or validation expectation are too unclear to support safe planning or handoff.

## Quality Bar

A strong output should:

- distinguish facts from assumptions
- avoid rewriting the whole ticket when a targeted readiness judgment is enough
- explain exactly which missing criteria matter and why
- ask for the smallest missing detail instead of turning the result into a long questionnaire
- make the next planner action obvious

## Failure and Ambiguity Handling

- Do not invent missing acceptance criteria.
- If the task is partly clear, say what is usable now and what still needs clarification.
- If runtime symptoms dominate the task, note that the issue may need troubleshooting before acceptance criteria can be finalized.
- If validation expectations are missing, call that out explicitly because it affects downstream handoff quality.
- If the environment is unclear, assume stage-first for planning but still mark the missing environment detail if it changes execution or validation.
