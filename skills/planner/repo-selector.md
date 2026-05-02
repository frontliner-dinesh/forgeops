---
name: repo-selector
description: Use when the agent needs to decide which ForgeOps repository or repositories should own a task, rank likely repo targets, explain the reasoning, and prepare a scoped repo-targeting recommendation for planning or handoff.
---

# Repo Selector

## Overview

Use this skill when the current task includes repo targeting uncertainty or when another agent needs a clean decision about where work belongs before implementation starts.

This skill is for repository decision-making and scope shaping. It does not perform implementation work.

## Inputs

Gather whatever is available from the current run:

- Jira ticket content or task summary
- relevant Confluence notes or architectural guidance
- known affected service, module, stack, or environment
- any mentioned files, directories, systems, or workflows
- known implementation constraints or acceptance criteria

Use Atlassian Rovo when Jira or Confluence context is needed to understand ownership, architecture, or delivery scope.
Use GitHub when repository structure, existing patterns, or file locations help confirm the correct target.

## Repository Decision Set

Choose among these repositories by default:

- `Forecast-5-Analytics/dna-terraform-modules`
- `Forecast-5-Analytics/dna-terraform-infrastructure`
- `Forecast-5-Analytics/dna-ansible-playbooks`

## Decision Rules

Apply these rules in order:

1. Choose `dna-terraform-modules` when the task changes reusable Terraform building blocks, shared abstractions, module interfaces, shared variables, outputs, or module-level conventions.
2. Choose `dna-terraform-infrastructure` when the task changes environment-specific composition, stack instantiation, rollout wiring, account or environment bindings, or the way existing modules are assembled for a target environment.
3. Choose `dna-ansible-playbooks` when the task changes host configuration, post-provisioning automation, operational playbooks, package or service configuration, or task execution logic on provisioned systems.
4. If the task spans more than one layer, recommend a split and explain the sequence.
5. If evidence is incomplete, provide a ranked repo hypothesis rather than forcing a single answer.

## Workflow

1. Read the task and identify what is actually changing: reusable module logic, environment composition, operational automation, or a combination.
2. Extract any direct clues such as repo names, file paths, module names, playbook references, environment names, or service ownership details.
3. Use Jira and Confluence context to understand architecture intent when the task wording is vague.
4. Use GitHub context when file layout or existing implementation patterns help distinguish between module, infrastructure, and playbook ownership.
5. Decide whether the task belongs in one repo or multiple repos.
6. If multiple repos are involved, define the split clearly and explain what belongs in each one.
7. Identify any ambiguity that should be resolved before implementation starts.
8. Return a concise repo-targeting recommendation suitable for planner output or specialist handoff.

## Output Contract

Return a concise result with these sections:

- Task summary
- Recommended repo or repos
- Repo ranking, if uncertain
- Why the work belongs there
- Likely affected paths or areas, if known
- Cross-repo split, if applicable
- Ambiguities or blockers
- Next planning or handoff action

## Quality Bar

A strong output should:

- make a clear repo recommendation instead of repeating the task back
- explain the reasoning in terms of ownership and change type
- call out when the task spans module, environment, and automation layers
- give a ranked hypothesis when certainty is limited
- stay scoped to the repositories that actually matter
- make the next step easier for the planner or builder

## Failure and Ambiguity Handling

- Do not pretend the repo choice is certain when evidence is weak.
- If the task appears to involve both reusable module work and environment wiring, recommend a split rather than collapsing everything into one repo.
- If the request mixes implementation planning with runtime symptoms, note the likely repo target but recommend a troubleshooter handoff if runtime evidence is still needed first.
- If no grounded repo decision can be made, state the smallest missing detail that would resolve the uncertainty.
