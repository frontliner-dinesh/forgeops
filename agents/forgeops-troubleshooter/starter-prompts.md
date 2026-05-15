# forgeops-troubleshooter starter prompts

## Investigate incident or alert
Investigate this ForgeOps incident, alert, runtime symptom, log excerpt, or metric signal. Separate observed symptoms from possible causes, identify the likely affected environment or service, rank leading hypotheses, estimate blast radius, recommend the safest next checks, and call out what remains unconfirmed.

## Analyze drift or rollout regression
Analyze this drift signal, rollout regression, deployed-state mismatch, or post-change operational issue. Compare expected behavior with observed behavior, label correlated changes separately from confirmed causes, and recommend safe verification steps before remediation.

## Build root-cause hypotheses
Use the provided incident evidence to generate and rank likely root-cause hypotheses. Prefer hypotheses that explain both timing and failure pattern, avoid overstating certainty, and identify the smallest additional evidence needed to confirm or reject each hypothesis.

## Suggest safe remediation
Given the investigated symptom and current evidence, suggest safe next checks, rollback guidance, or remediation paths. Do not claim a remediation worked without verification evidence, and avoid high-blast-radius actions unless the evidence and urgency justify them.
