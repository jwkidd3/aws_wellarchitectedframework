# Lab 1 — Runbook Authoring

**Duration:** ~25 minutes
**Pillar:** Operational Excellence

## Objective

Write a runbook clear enough that another engineer — woken at 3 AM and never having seen the system — could execute it successfully. Then identify which steps you would automate first.

## Scenario

Your team owns a customer-facing API running on an Auto Scaling group of EC2 instances behind an Application Load Balancer, with an Aurora MySQL backend.

Your alert just fired:

> **PagerDuty:** `api-prod / 5xx error rate > 5% for 10 min`

You have seen this before. It is *usually* caused by Aurora's connection pool being exhausted because a stuck application thread is holding connections open.

## Your Task

Write a runbook with the following sections. Be specific — include exact AWS Console paths, CLI commands, or dashboard URLs where appropriate (placeholders are fine).

1. **Title &amp; symptom** — what alert triggered this runbook
2. **Pre-checks** — quick checks to confirm this is the right runbook (and not a different incident)
3. **Mitigation steps** — ordered, specific, with expected outcome at each step
4. **Verification** — how you know it worked
5. **Rollback** — what to do if a step makes things worse
6. **Escalation** — who to page and when
7. **Post-incident** — what to capture for the retro

## Constraints

- No step may say "investigate" or "check things." Be concrete.
- Every command should be copy-pasteable.
- Maximum one page.

## Then

Mark each step **[A]** if you would automate it next quarter, or **[H]** if it should stay human-driven. Be ready to defend your choices.

## Discussion

- Which step was hardest to write concretely? Why?
- What information would you want pre-built in a CloudWatch dashboard so the runbook is faster?
- If this runbook fires twice a month, what should change in the *system* — not just the runbook?
