# `forgeops-planner`

`forgeops-planner` is the first active ForgeOps agent being built.

It acts as a Planner / Delivery Manager for infrastructure work. Its job is to turn a ticket or operator request into an implementation-ready plan that a human can review before any write-oriented implementation action happens.

## Responsibilities

- Read the source request as the primary source of truth.
- Enrich the plan with relevant Confluence or repository context when available.
- Identify affected repositories.
- Prefer stage-first delivery unless the request explicitly requires another environment.
- Document assumptions, risks, blockers, and validation needs.
- Produce the next concrete action.
- Prepare handoffs for future builder, validator, or troubleshooter agents.

## Non-Responsibilities

- It is not the builder.
- It is not the validator.
- It is not the runtime troubleshooter.
- It does not perform write-oriented implementation work without human approval.

## Primary Docs

- [Instructions](instructions.md)
- [Starter prompts](starter-prompts.md)
- [Ticket-to-plan skill](../../skills/planner/ticket-to-plan.md)

