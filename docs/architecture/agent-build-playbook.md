# Agent Build Playbook

## Purpose

This document explains how to build ForgeOps agents consistently in ChatGPT Agent Builder while keeping the GitHub repo in sync.

## Standard Build Loop

For each new ForgeOps agent:

1. Create the new agent in the editor
2. Name it using the ForgeOps naming scheme:
   - forgeops-planner
   - forgeops-builder
   - forgeops-validator
   - forgeops-troubleshooter
3. Rewrite its instructions around its specific role
4. Update its short description and starter prompts
5. Add only the minimum useful first skills
6. Test the role boundary before adding more skills
7. Sync the changes back to GitHub

## Role First, Skills Second

Do not start by attaching many skills.

First define:
- what the agent owns
- what it does not own
- what inputs it expects
- what outputs it should produce
- what other ForgeOps agents it should hand work to

Then add only the first 2-4 skills needed to make the role reliable.

## Recommended First Skills By Agent

### forgeops-planner
Current attached skills:
- ticket-to-plan
- repo-selector
- acceptance-criteria-checker
- specialist-handoff-writer

### forgeops-builder
Recommended first skills:
- implementation-drafter
- path-scoper
- pr-summary-writer

Codex-handoff posture:
- forgeops-builder may be configured as a Codex-handoff agent.
- This means shaping outputs toward coding-ready prompts and patch-oriented plans.
- Codex-handoff output should include target repo, branch expectation when known, likely files, exact change objective, constraints, validation still needed, and blockers.
- This is still not the same as a native Codex runtime or tool inside the editor.
- This does not move planner, validator, or troubleshooter responsibilities into builder.

GitHub approval posture:
- forgeops-builder can use GitHub for implementation work.
- GitHub write actions must require human confirmation.
- This approval posture matches ForgeOps' handoff-first and human-approved write model.
- Previewing and drafting can proceed without pretending validation or deployment happened.

### forgeops-validator
Recommended first skills:
- acceptance-criteria-fulfillment-checker
- infra-diff-reviewer
- rollback-and-risk-reviewer

### forgeops-troubleshooter
Recommended first skills:
- runtime-signal-reader
- root-cause-hypothesis-builder
- safe-remediation-suggester

## How To Decide Whether A Skill Should Be Added

Add a skill only if it:
- improves repeatability
- reduces ambiguity
- protects role boundaries
- helps produce a consistent output shape

Do not add a skill just because it sounds useful in theory.

## GitHub Sync Rule

After every meaningful editor change:
- sync the corresponding architecture, instruction, or skill spec to GitHub
- commit small, readable changes
- push the commit to origin main after committing
- keep the repo as the design history

## Standard Codex Handoff Pattern

When an editor change is made, create a Codex prompt that includes:
- repo URL
- branch name
- exact file path to create or update
- exact content to write
- commit message
- instruction to push the commit to origin main after committing
- request to print commit hash, pushed branch, and short summary

## Reusable Codex Prompt Template

Use this structure:

Update the ForgeOps repo to match the latest agent/editor change.

Repository:
- https://github.com/frontliner-dinesh/forgeops.git
- branch: main

Create or update these files:
- <file paths>

Use this exact content:
<paste exact content>

Then:
1. commit the change
2. use commit message: "<commit message>"
3. push the commit to origin main
4. print the commit hash, pushed branch, and a short summary

## Agent Chat Bootstrap Guidance

When starting work in a new agent chat, reference:
- docs/architecture/forgeops-master-plan.md
- docs/architecture/agent-build-playbook.md

That should be enough context for continuing the ForgeOps build without restating the whole architecture each time.

## Current Recommendation

The next active build target after forgeops-planner is:
- forgeops-builder

Start builder with:
- Codex-handoff role and boundary definition
- rewritten instructions
- updated description and starter prompts
- only the first few implementation-focused skills
