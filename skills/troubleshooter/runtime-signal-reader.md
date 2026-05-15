---
name: runtime-signal-reader
description: Use when the request is about alerts, incidents, runtime symptoms, drift, health regressions, deployment mismatches, logs, alarms, or metrics and the agent needs to separate observed signals from interpretation before drawing conclusions.
---

# Runtime Signal Reader

## Overview

Use this skill to read operational evidence before forming a diagnosis.

This skill separates observed runtime signals from interpretation so `forgeops-troubleshooter` does not jump from symptoms to root cause without evidence.

## When To Use

Use `$runtime-signal-reader` for:
- alerts and incidents
- runtime symptoms
- drift or deployed-state mismatches
- health regressions
- deployment mismatches
- logs, alarms, metrics, or failed checks

Do not use this skill to review diffs or proposed code changes. Route review work to `forgeops-validator`.

## Workflow

1. Identify each observed signal exactly as provided.
2. Separate symptom, timing, environment, service, and source of evidence.
3. Call out missing or unclear evidence.
4. Distinguish confirmed observations from assumptions and interpretation.
5. Identify which signals are strong, weak, stale, or conflicting.
6. Recommend the safest next evidence to gather.

## Output Contract

Return these sections:
- Observed signals
- Likely affected environment or service
- Evidence source
- Confirmed facts
- Assumptions or unknowns
- Signal interpretation
- Safest next evidence to gather

## Quality Bar

A strong result should:
- avoid inventing runtime evidence
- keep symptoms separate from causes
- preserve timing and source details
- call out uncertainty plainly
- recommend low-risk verification steps before remediation
