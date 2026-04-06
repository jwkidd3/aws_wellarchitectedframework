# Lab 3 — Disaster Recovery Pattern Selection

**Duration:** ~25 minutes
**Pillar:** Reliability

## Objective

For each of three workloads, choose a DR pattern (Backup &amp; Restore, Pilot Light, Warm Standby, or Active/Active), justify it against the RTO/RPO and budget, and identify what you would test to prove it works.

## DR Pattern Reference

| Pattern             | Typical RTO | Typical RPO | Relative Cost |
| ------------------- | ----------- | ----------- | ------------- |
| Backup &amp; Restore | Hours       | Hours       | $             |
| Pilot Light         | 10s of min  | Minutes     | $$            |
| Warm Standby        | Minutes     | Seconds–min | $$$           |
| Active/Active       | Seconds     | Near-zero   | $$$$          |

## Workload A — Internal HR Reporting Tool

- ~50 internal users, business-hours only
- Aurora MySQL backend, ~20 GB
- Outage tolerable for a workday; data loss must be < 24 hours
- Budget: minimal — IT chargeback only

## Workload B — Customer-Facing E-Commerce Storefront

- ~5,000 concurrent shoppers at peak, 24×7
- DynamoDB + Lambda + CloudFront
- Every minute of downtime = lost revenue and brand damage
- Compliance: data must stay in-region or in approved regions
- Budget: significant — revenue protection justifies it

## Workload C — Real-Time Trading Platform

- Tier-0 financial workload
- Sub-second order routing
- Any data loss is unacceptable; any meaningful downtime triggers regulatory reporting
- Budget: essentially open

## Tasks

For each workload (A, B, C):

1. **Pattern choice** — pick one DR pattern and justify in 2–3 sentences
2. **Target RTO and RPO** — be specific
3. **AWS services** — what you'd actually use (e.g., AWS Backup, cross-region replication, Route 53 ARC, Aurora Global Database, S3 CRR, DynamoDB Global Tables)
4. **What you would test** — one game-day scenario per workload
5. **Top risk** — the thing most likely to break the plan

## Discussion

- Did anyone pick *Active/Active* for Workload A? Why not?
- For Workload B, what's the trap of just "checking the box" with cross-region replication but never testing failover?
- How does the DR pattern affect Pillar 5 (Cost) and Pillar 6 (Sustainability)?
