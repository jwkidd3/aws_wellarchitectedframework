# Lab 7 — Mini Well-Architected Review (Capstone)

**Duration:** ~45 minutes
**Pillars:** All six

## Objective

Run a lightweight Well-Architected Review against a sample workload, assign risk levels across all six pillars, and produce a prioritized remediation roadmap.

Work in pairs or small groups. The point is the *conversation* the framework forces — not a perfect score.

## The Sample Workload — "OrderFlow"

OrderFlow is a B2B order-management SaaS, ~3 years old. The team inherited it last quarter.

**Architecture**

- Single AWS account, `us-east-1` only
- ALB → 6 × `m5.large` EC2 instances (fixed, no Auto Scaling) running a Node.js app
- Aurora MySQL cluster, 1 writer + 1 reader, single AZ
- S3 bucket for customer file uploads (no lifecycle rules)
- A Jenkins box on EC2 deploys via SSH and shell scripts
- CloudWatch metrics on by default; no custom dashboards
- IAM: 14 IAM users (humans + a couple of CI bots), several with `AdministratorAccess`
- Backups: nightly Aurora snapshot, retained 7 days, never tested
- One runbook in a Google Doc, last updated 14 months ago
- Cost: ~$11k/month, no Savings Plans, no tagging policy
- No CDN; static assets served from EC2
- Customers report intermittent slow page loads at peak

## Tasks

For **each pillar**, do the following:

1. **Note 2–3 findings** — specific issues you'd flag
2. **Assign a risk** — High / Medium / None
3. **Pick the single highest-impact fix** for that pillar

Then, across all six pillars:

4. **Build a roadmap** — top 5 items overall, in order, with rough effort (S/M/L)
5. **Identify cross-pillar wins** — fixes that help two or more pillars
6. **Identify trade-offs** — where fixing one pillar hurts another, and how you'd negotiate

## Deliverable

A one-page summary you'd present to the engineering manager:

- The 3 things you'd do this sprint
- The 2 things you'd do this quarter
- The 1 thing leadership needs to know about *now*

## Discussion

- Where did your team disagree most? Was it about priority or about *facts*?
- How would the answers change if OrderFlow were Tier-0 financial software? If it were an internal tool with 20 users?
- Which pillar was hardest to assess from this description alone? What would you need to ask the team to know more?
