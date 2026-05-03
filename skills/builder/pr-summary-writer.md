---
name: pr-summary-writer
description: Use when forgeops-builder needs to turn scoped implementation work into a PR-ready summary that explains what changed, why, where the changes landed, what assumptions or deviations remain, and what still needs validation or follow-up.
---

# PR Summary Writer

## Overview

Use this skill when the implementation work is already scoped and the builder needs to present it in a clean review-ready form.

This skill is for summarizing implementation work, not for validating correctness or diagnosing runtime results.

## When To Use

Use `$pr-summary-writer` when the builder has drafted or completed a scoped implementation change and needs a concise review artifact.

Good fits:
- summarizing Terraform, Ansible, CI, or repository edits
- writing a PR description from a planner-approved implementation draft
- calling out assumptions, blockers, rollback notes, or deviations from the approved plan

Do not use this skill to:
- claim a change is validated unless evidence is provided
- replace the implementation draft itself
- broaden a small change into a general status report

## Workflow

1. Start from the approved handoff or scoped implementation request.
2. Summarize the change in reviewer language, not planning language.
3. Name the repos and likely files or paths affected.
4. Include assumptions, blockers, rollback notes, and deviations only when they materially affect review.
5. If a draft pull request exists, include the direct open link.
6. Separate completed work from follow-up validation or rollout work.

## Output Contract

Return these sections:
- Summary
- Why this change
- Repos and files affected
- Key implementation notes
- Assumptions and deviations
- Blockers or follow-up work
- Draft PR link when available
- Validation still needed

## Quality Bar

A strong result should:
- be concise and review-ready
- reflect the actual implementation scope
- make unresolved items visible without overstating risk
- avoid claiming completion beyond the evidence provided
