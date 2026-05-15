---
name: safe-remediation-suggester
description: Use when the user needs safe next checks, rollback guidance, or remediation options after an operational issue has been investigated but the correct fix is not yet fully confirmed.
---

# Safe Remediation Suggester

## Overview

Use this skill when enough investigation has happened to discuss next checks or remediation paths, but the fix is not fully confirmed.

This skill prioritizes low-blast-radius verification, rollback thinking, and clear uncertainty over quick speculative fixes.

## When To Use

Use `$safe-remediation-suggester` for:
- safe next checks after an incident investigation
- rollback or mitigation options
- remediation choices under uncertainty
- post-change operational issues
- drift or rollout regression follow-up

Do not use this skill to claim a remediation worked unless verification evidence is provided.

## Workflow

1. Summarize the current evidence and leading hypothesis.
2. Identify the blast radius and operational risk.
3. Recommend safe next checks before remediation when possible.
4. Suggest remediation paths with confidence and tradeoffs.
5. Flag high-blast-radius actions and require stronger evidence before recommending them.
6. Define verification evidence needed after any remediation.

## Output Contract

Return these sections:
- Current evidence
- Leading hypothesis
- Blast-radius assessment
- Safest next checks
- Possible remediation paths
- Risk and rollback notes
- Verification needed
- What remains unconfirmed

## Quality Bar

A strong result should:
- prefer safe verification before action
- avoid casual high-blast-radius recommendations
- label uncertainty and confidence clearly
- include rollback and verification thinking
- avoid broad code changes when operational checks should come first
