# `ticket-to-plan` Skill

## Purpose

Convert a Jira ticket or infrastructure request into an implementation-ready ForgeOps plan for human review.

The skill is owned by `forgeops-planner`, the first active ForgeOps agent. It should produce a clear plan without performing write-oriented implementation work.

## Inputs

- Jira ticket ID or ticket content.
- Request summary if no ticket is available.
- Relevant Confluence links or excerpts when available.
- Target environment, if specified.
- Known affected service, module, stack, or repository.
- Any operator constraints, deadlines, or acceptance criteria.

## Workflow

1. Read the ticket or request as the source of truth.
2. Identify the requested outcome and target environment.
3. Default to stage-first delivery when the environment is absent or ambiguous.
4. Enrich with Confluence context when it clarifies architecture, procedures, ownership, or past decisions.
5. Identify likely affected repositories:
   - `Forecast-5-Analytics/dna-terraform-modules`
   - `Forecast-5-Analytics/dna-terraform-infrastructure`
   - `Forecast-5-Analytics/dna-ansible-playbooks`
6. Separate known facts from assumptions.
7. Identify risks, blockers, and missing information.
8. Draft an implementation-ready plan.
9. Define validation expectations.
10. State the next concrete action and whether human approval is required before that action.

## Output Contract

Return a concise plan with these sections:

- Summary.
- Source ticket or request.
- Target environment.
- Affected repos.
- Implementation plan.
- Assumptions.
- Risks.
- Blockers.
- Validation expectations.
- Handoff recommendation, if builder, validator, or troubleshooter involvement is needed.
- Next concrete action.

## What Good Looks Like

- The plan is specific enough for a builder or human operator to continue.
- The target environment is explicit and stage-first by default.
- Affected repositories are named instead of implied.
- Assumptions are labeled as assumptions.
- Risks are concrete and tied to the proposed work.
- Blockers are actionable.
- Validation expectations are clear enough to execute.
- The next concrete action is a single, reviewable step.
- The plan does not perform write-oriented implementation work without human approval.

## Failure / Ambiguity Handling

If the ticket or request is incomplete, do not invent missing facts. State what is missing, make conservative assumptions when useful, and identify the smallest next action needed to unblock planning.

If the target environment is unclear, assume stage for planning purposes and call out that assumption.

If the affected repository is unclear, provide a ranked repo hypothesis and explain why each repo may be involved.

If the request appears production-impacting, security-sensitive, or irreversible, mark it as requiring explicit human approval before any write-oriented implementation action.

If runtime symptoms dominate the request, prepare a planner-to-troubleshooter handoff instead of trying to diagnose deeply within the planner role.

