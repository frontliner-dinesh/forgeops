# ForgeOps System Overview

ForgeOps is a lightweight multi-agent infrastructure delivery system. Its source of truth lives in this repo and should stay easy to evolve as the agent set, skills, and delivery contracts mature.

The system is intended to help turn infrastructure work requests into implementation-ready plans, targeted repository changes, validation guidance, and troubleshooting follow-up. It should support human operators rather than hide delivery decisions behind automation.

## Current State

`forgeops-planner` is the first active agent being built.

The other agents are intentionally represented as placeholders until their responsibilities and handoff needs are proven by planner output:

- `forgeops-builder`
- `forgeops-validator`
- `forgeops-troubleshooter`

## Delivery Model

ForgeOps starts with planning. The planner interprets intake, enriches it with available context, identifies target repositories, and produces a concrete plan that a human can approve before any write-oriented implementation action happens.

The default delivery posture is stage-first. Production-impacting work should be called out explicitly and should require stronger confirmation than stage-only work.

## Design Principles

- Keep the system lightweight and source-controlled.
- Prefer explicit handoffs over implicit agent behavior.
- Keep agent scopes narrow and named.
- Make assumptions, risks, blockers, and next actions visible.
- Require human approval before write-oriented implementation work.
- Avoid company-specific CI/CD, compliance, and governance rules until the system needs them.

## High-Level Flow

1. Intake arrives from a ticket, operator request, or troubleshooting context.
2. `forgeops-planner` converts the request into an implementation-ready plan.
3. A human reviews and approves the next write-oriented action.
4. Future agents may implement, validate, or troubleshoot using planner handoff contracts.

