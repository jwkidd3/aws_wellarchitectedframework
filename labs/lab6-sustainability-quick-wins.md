# Lab 6 — Sustainability Quick Wins

**Duration:** ~20 minutes
**Pillar:** Sustainability

## Objective

Review a small reference architecture, list sustainability improvements you would make, and show how each one also improves at least one other pillar (usually Cost or Performance).

## The Architecture

A B2B SaaS analytics product:

- **Region:** `us-east-1` only (chosen years ago, no specific reason)
- **Web tier:** 12 × `m5.xlarge` EC2 instances behind an ALB, fixed size 24×7. Average CPU 12%.
- **API tier:** 8 × `c5.2xlarge` EC2 instances, fixed size 24×7. Average CPU 18%.
- **Background workers:** 6 × `m5.2xlarge` EC2 instances. Process a nightly batch in ~2 hours; idle the other 22 hours.
- **Database:** Aurora MySQL, 2 × `db.r5.4xlarge` writers/readers (production); plus one identical clone for staging running 24×7
- **Storage:** ~45 TB in S3 Standard. About 70% has not been accessed in 6+ months. No lifecycle policies.
- **Logging:** CloudWatch Logs with no retention policy set
- **CDN:** None — every request hits the ALB, including for the static dashboard JS bundle

## Tasks

1. **List 6–8 sustainability improvements.** For each:
   - What you'd change
   - Which other pillar it benefits (Cost / Performance / Reliability / Operational Excellence)
   - Rough effort: small / medium / large
2. **Pick the top 3** to do this quarter — defend the prioritization.
3. **Identify one improvement that would *worsen* another pillar** if done carelessly, and how you'd avoid that trap.

## Hints

- Look for: idle capacity, oversized instances, missing auto-scaling, missing storage tiering, missing CDN, missing log retention, region choice for non-latency-sensitive work, instance family generation (Graviton)

## Discussion

- Did your top 3 align with what Cost Optimization (Lab 5) would have prioritized? Why is that?
- For the worker tier — what architectural change (not just sizing) would dramatically improve sustainability?
  *Hint: do those workers need to be EC2 at all?*
- Sustainability is often called "Cost Optimization with a green hat." Where does that analogy break down?
