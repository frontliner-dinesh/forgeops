---
name: path-scoper
description: Use when forgeops-builder needs to map an approved handoff or scoped build request to the most likely repositories, directories, files, modules, roles, workflows, and CI paths before drafting changes.
---

# Path Scoper

## Overview

Use this skill to identify where implementation work most likely belongs before drafting edits.

This skill helps the builder stay narrow and repo-appropriate. It does not draft broad changes on its own.

## When To Use

Use `$path-scoper` when the request is specific enough to implement but the likely repo paths, modules, or files still need to be mapped.

Good fits:
- choosing between the Terraform modules repo and the infrastructure repo
- identifying likely Ansible roles, playbooks, or inventory-related files
- narrowing implementation to likely CI workflows, pipeline files, or repository config
- separating multi-repo work into small path-based change sets

Do not use this skill to:
- invent missing product or operational requirements
- redesign the implementation approach at a planning level
- claim that the identified paths are confirmed when they are inferred

## Workflow

1. Read the request for explicit repo, environment, and component clues.
2. Start with the explicit repo if one is named.
3. If no repo is named, infer the most likely repo using ForgeOps defaults.
4. Identify the likely directories, modules, files, roles, workflows, or CI surfaces involved.
5. If multiple path candidates exist, rank them briefly and explain why.
6. Keep the output narrow enough for implementation drafting to continue without re-scoping the whole request.

## Repo Targeting Defaults

Use these defaults unless the request says otherwise:
- `Forecast-5-Analytics/dna-terraform-modules` for shared reusable Terraform module logic
- `Forecast-5-Analytics/dna-terraform-infrastructure` for environment or stack wiring and rollout composition
- `Forecast-5-Analytics/dna-ansible-playbooks` for configuration management, host automation, and operational playbooks

## Output Contract

Return these sections:
- Scope summary
- Most likely repo
- Likely directories or files
- Secondary path candidates
- Assumptions
- Open path questions
- Recommended next implementation focus

## Quality Bar

A strong result should:
- make repo targeting explicit
- distinguish likely paths from confirmed paths
- reduce implementation ambiguity
- prefer the smallest credible path set over an exhaustive repository tour
