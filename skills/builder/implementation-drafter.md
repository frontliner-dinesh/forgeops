---
name: implementation-drafter
description: Use when forgeops-builder needs to turn an approved planner handoff or a clearly scoped direct build request into a small, reviewable implementation draft with likely files, scoped Terraform or Ansible changes, assumptions, blockers, and a PR-ready summary, using GitHub as the default repo surface unless the run explicitly provides a checked-out local repo.
---

# Implementation Drafter

## Overview

Use this skill when the task is to draft implementation work for ForgeOps.

This skill is for scoped implementation drafting. It is not for replanning the request, validating whether the change is correct, or diagnosing runtime behavior.

## When To Use

Use `$implementation-drafter` when the request includes either:
- an approved forgeops-planner handoff, or
- a clearly scoped direct build request that is already narrow enough to implement

Good fits:
- drafting Terraform changes for a named module or stack
- drafting Ansible changes for a known playbook, role, or host workflow
- drafting CI or repository changes tied to a specific implementation request
- turning a handoff into a small implementation sequence and likely file edits

Do not use this skill to:
- redo planning from scratch
- decide whether a proposed change satisfies acceptance criteria
- claim runtime diagnosis or validation without evidence

## Inputs To Preserve

When available, preserve these details from the request or handoff:
- target environment
- affected repos
- likely files, modules, roles, or infrastructure areas
- assumptions and open questions
- risks and rollback considerations
- validation expectations
- next concrete action

If the environment is unclear, default to stage-first and state that assumption explicitly.

## Repo Access Rules

- Use configured GitHub access as the default source for repo contents, branches, pull requests, and repository state.
- Do not assume `/workspace` is a checked-out target repo.
- Do not assume a local feature branch, local git metadata, or `gh` CLI access exists unless the run clearly provides that environment.
- Only rely on a local checkout when the run explicitly includes the target repository in the workspace.
- If repo state needed for a write or PR action is missing, ask for the smallest missing repo or branch detail instead of implying that a local checkout should already exist.

## Workflow

1. Identify the target repo and the narrowest approved scope.
2. Determine the likely files, modules, roles, workflows, or CI surfaces involved.
3. Preserve planner constraints and assumptions instead of reframing the request.
4. Draft the smallest repo-appropriate change that satisfies the approved scope.
5. If repo context is incomplete, make the minimum reasonable structural assumption and label it clearly.
6. End with a short PR-ready summary plus blockers or follow-up work.

## Repo Targeting Defaults

Use these defaults unless the request says otherwise:
- `Forecast-5-Analytics/dna-terraform-modules` for shared reusable Terraform building blocks
- `Forecast-5-Analytics/dna-terraform-infrastructure` for environment-specific composition and infrastructure wiring
- `Forecast-5-Analytics/dna-ansible-playbooks` for host configuration, post-provisioning automation, and operational playbooks

If more than one repo is involved, separate the draft by repo and keep each change set narrow.

## Implementation Rules

- When referencing a Terraform module source, prefer the latest stable Git tag rather than a branch reference unless the handoff explicitly calls for a different source strategy.
- When introducing a new module or backend-related abstraction, prefer a name that clearly reflects the bucket or state resource it manages.

## Output Contract

Return a concise implementation draft with these sections:
- Summary
- Target repo
- Likely files or paths to change
- Implementation steps
- Draft changes
- Assumptions
- Blockers
- Risks and rollback notes
- PR-ready summary

## Quality Bar

A strong result should:
- stay implementation-focused
- prefer small, reviewable changes over broad rewrites
- preserve planner intent
- separate confirmed facts from assumptions
- avoid claiming validation or runtime certainty without evidence
