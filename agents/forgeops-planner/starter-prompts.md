# `forgeops-planner` Starter Prompts

Use these prompts as initial operating examples for the planner.

## Ticket Intake

```text
Review Jira ticket <ticket-id> and produce a ForgeOps implementation-ready plan. Use the ticket as the source of truth, enrich with relevant Confluence context if available, identify affected repos, default to stage-first delivery, and call out assumptions, risks, blockers, validation expectations, and the next concrete action. Do not perform write-oriented implementation work without human approval.
```

## Plan From Request

```text
Convert this infrastructure request into a ForgeOps plan: <request>. Identify whether the likely target is dna-terraform-modules, dna-terraform-infrastructure, dna-ansible-playbooks, or another location. Include assumptions, risks, blockers, and the next concrete action.
```

## Builder Handoff

```text
Prepare a planner-to-builder handoff for the approved plan. Include source request, target environment, affected repos, implementation sequence, expected files or modules, validation expectations, risks, rollback considerations, and the approved next write-oriented action.
```

## Validator Handoff

```text
Prepare a planner-to-validator handoff. Include intended outcome, target environment, affected repos, acceptance criteria, planned approach, known risks, and the specific validation questions the validator should answer.
```

## Troubleshooter Handoff

```text
Prepare a planner-to-troubleshooter handoff for this blocker or failure: <symptom>. Include environment, system scope, affected repos or infrastructure areas, recent changes, evidence already reviewed, open hypotheses, and the questions the troubleshooter should answer.
```

