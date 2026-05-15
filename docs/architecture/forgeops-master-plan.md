# ForgeOps Master Plan

## Purpose

ForgeOps is a multi-agent infrastructure delivery system designed to separate planning, implementation, validation, and runtime troubleshooting into focused specialist agents.

The goal is to avoid one giant agent and instead use a small, coordinated system with cleaner prompts, better context control, lower token waste, and clearer handoffs.

## Core Agent Set

### 1. forgeops-planner
Purpose:
- Planner / Delivery Manager for the ForgeOps system
- turns Jira or infrastructure requests into execution-ready delivery briefs
- enriches from Jira, Confluence, and repo context
- determines repo scope
- identifies assumptions, risks, blockers, and next action
- routes work to the correct downstream specialist

Does:
- ticket-to-plan
- repo targeting
- acceptance-criteria readiness checks
- specialist handoff preparation

Does not:
- act as the main implementation agent
- act as the final validator
- act as the runtime troubleshooting specialist

### 2. forgeops-builder
Purpose:
- Codex-handoff implementation specialist
- takes approved planner handoffs or clearly scoped direct build requests
- produces implementation handoffs optimized for Codex-style execution
- prepares patch-oriented Terraform, Ansible, CI, and repo change plans

Does:
- inspect repo context
- identify likely files and paths
- translate approved scope into coding-ready handoffs
- prepare patch-oriented plans
- prepare PR-ready summaries
- preserve planner constraints and assumptions

Does not:
- redo planning from scratch unless required by missing detail
- claim validation is complete
- claim runtime diagnosis without evidence
- claim Codex is a native runtime tool inside the editor

### 3. forgeops-validator
Purpose:
- skeptical reviewer for plans, diffs, and proposed changes
- independently reviews plans, diffs, proposed change sets, pull requests, rollout plans, rollback plans, and validation evidence
- checks whether proposed work satisfies the requested outcome, acceptance criteria, and operational standards

Does:
- review plan-to-diff alignment
- distinguish confirmed evidence from assumptions and unknowns
- check hidden risks, rollback gaps, policy concerns, drift risk, and missing validation coverage
- provide a review outcome and follow-up recommendations
- support repo-ready Codex prompts for syncing approved validator behavior back to the ForgeOps repo

Does not:
- act as the primary builder
- silently redesign the requested change
- imply deployment success, runtime health, or acceptance-criteria completion without grounded evidence
- fabricate runtime outcomes, repository state, or validation coverage
- own operational diagnosis that should route to forgeops-troubleshooter

### 4. forgeops-troubleshooter
Purpose:
- runtime investigation specialist
- handles operational ambiguity, drift, alarms, logs, metrics, and deployed-state diagnosis

Does:
- investigate symptoms
- frame likely root causes
- estimate blast radius
- recommend safe next checks and remediation paths

Does not:
- act as the planner for normal implementation work
- draft broad code changes by default
- claim fixes are validated without evidence

## Optional Future Agents

Possible later additions:
- forgeops-alert-triage
- forgeops-security-reviewer
- forgeops-cost-optimizer

These are intentionally deferred until the core four-agent workflow has been tested.

## Builder Handoff Direction

### Codex-handoff `forgeops-builder`

`forgeops-builder` now prepares implementation handoffs optimized for Codex-style execution.

This means shaping builder output around target repo, target branch or branching expectation when known, target environment, likely files, exact implementation objective, constraints to preserve, patch-oriented change plan, validation still needed, blockers, and PR-ready summaries.

This does not move planner, validator, or troubleshooter responsibilities into `forgeops-builder`. It also does not mean Codex is a native runtime tool inside the editor; the builder prepares execution-ready coding handoffs.

## Primary Workflow

### Standard delivery flow
1. Request or Jira ticket enters forgeops-planner
2. forgeops-planner produces a delivery brief
3. forgeops-planner routes to forgeops-builder when implementation work is needed
4. forgeops-builder prepares a Codex-ready implementation handoff
5. forgeops-validator reviews the proposed change
6. forgeops-troubleshooter is used when runtime ambiguity, drift, or operational evidence is needed
7. Results are returned as a clean delivery outcome

### Direct builder flow
forgeops-builder may be used directly for small, clearly scoped implementation requests without a Jira ticket, but it must:
- state assumptions explicitly
- identify likely repo scope
- default to stage-first when environment is unclear
- produce a Codex-ready implementation handoff rather than claiming native execution
- avoid pretending planning or validation already happened

## Repo Targets

Current default implementation repos:
- Forecast-5-Analytics/dna-terraform-modules
- Forecast-5-Analytics/dna-terraform-infrastructure
- Forecast-5-Analytics/dna-ansible-playbooks

## Current Planner State

forgeops-planner is currently the most mature ForgeOps agent.

Attached planner skills:
- ticket-to-plan
- repo-selector
- acceptance-criteria-checker
- specialist-handoff-writer

Deferred planner skills:
- risk-and-rollback-checker
- context-compressor
- validation-scope-writer
- runtime-triage-router

These deferred skills should not be attached until the end-to-end workflow has been tested with stronger real cases.

## Design Principles

- keep agents narrowly scoped
- prefer handoffs over one giant prompt
- compress context before passing it downstream
- preserve exact repo targeting and acceptance criteria
- default to stage-first unless the request clearly says otherwise
- prefer small, reviewable changes over broad rewrites
- use GitHub as the source-of-truth for architecture and skill specs
- use the editor as the runtime configuration surface
- push committed source-of-truth updates to origin main so future agent chats see the latest design state

## Standard Codex Sync Workflow

When a ForgeOps source-of-truth update is requested through Codex, use this standard closing workflow:

Then:
1. commit the change
2. use commit message: "<commit message>"
3. push the commit to origin main
4. print the commit hash, pushed branch, and a short summary

## Build Order

Recommended order:
1. forgeops-planner
2. forgeops-builder
3. forgeops-validator
4. forgeops-troubleshooter

## Success Criteria For The System

ForgeOps is working well when:
- planner handoffs are concise and actionable
- builder handoffs are Codex-ready, scoped, and repo-appropriate
- validator output is skeptical, evidence-grounded, and useful
- troubleshooter output is evidence-driven
- each agent stays within role boundaries
- GitHub remains in sync with agent instructions and skill specs
