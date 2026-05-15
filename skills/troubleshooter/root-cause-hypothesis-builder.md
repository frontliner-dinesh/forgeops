---
name: root-cause-hypothesis-builder
description: Use when the agent already has incident evidence and needs to generate, compare, and rank likely root-cause hypotheses without overstating certainty.
---

# Root Cause Hypothesis Builder

## Overview

Use this skill after runtime evidence has been gathered and the next step is to reason about likely causes.

This skill builds ranked hypotheses. It does not confirm root cause without evidence and does not claim remediation success.

## When To Use

Use `$root-cause-hypothesis-builder` when the request includes:
- incident evidence
- drift or health regression signals
- deployment timing
- logs, metrics, alarms, failed checks, or symptom descriptions
- expected behavior and observed behavior

Do not use this skill when the request is primarily a diff review or acceptance-criteria review. Route that to `forgeops-validator`.

## Workflow

1. Restate the observed symptom and affected scope.
2. Identify evidence that constrains the diagnosis.
3. Generate plausible hypotheses.
4. Rank hypotheses by likelihood and fit to timing plus failure pattern.
5. Label correlated changes as correlated unless evidence supports causality.
6. Identify what would confirm or reject each leading hypothesis.
7. Recommend the safest next checks.

## Output Contract

Return these sections:
- Observed symptom
- Evidence reviewed
- Leading hypotheses
- Why each hypothesis fits
- What would confirm or reject it
- Blast-radius considerations
- Safest next checks
- What remains unconfirmed

## Quality Bar

A strong result should:
- rank hypotheses without overstating certainty
- explain both timing and failure pattern
- separate cause, symptom, impact, and remediation
- avoid broad remediation before safe verification
- make uncertainty explicit
