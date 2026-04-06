# Lab 5 — Cost Allocation Analysis

**Duration:** ~30 minutes
**Pillar:** Cost Optimization

## Objective

Read a sample monthly AWS cost report, identify the top spenders and obvious waste, and recommend three concrete optimizations you would prioritize first.

## Scenario

You inherited an AWS account for a mid-size SaaS application. Finance forwarded last month's bill totaling **$24,830**. Below is the breakdown by service and tag.

## Cost by Service (last month)

| Service              | Cost (USD) | % of Bill |
| -------------------- | ---------: | --------: |
| EC2 — On-Demand      |   $9,420   |   38.0%   |
| RDS (Aurora MySQL)   |   $4,110   |   16.6%   |
| S3                   |   $2,950   |   11.9%   |
| Data Transfer Out    |   $2,180   |    8.8%   |
| EBS Volumes          |   $1,640   |    6.6%   |
| NAT Gateway          |   $1,230   |    5.0%   |
| CloudWatch Logs      |     $980   |    4.0%   |
| ELB                  |     $760   |    3.1%   |
| Lambda               |     $310   |    1.2%   |
| Other                |   $1,250   |    5.0%   |
| **Total**            | **$24,830**| **100%**  |

## Cost by `env` Tag

| env tag    | Cost (USD) |
| ---------- | ---------: |
| prod       |  $13,420   |
| staging    |   $4,890   |
| dev        |   $4,720   |
| (untagged) |   $1,800   |

## Notes from a Quick Walk-Through

- **EC2:** 24 instances. 8 of them are `m5.2xlarge` running at average 9% CPU. None are on a Savings Plan.
- **RDS:** 4 Aurora clusters. Two are tagged `dev` and run 24×7. No reserved capacity purchased.
- **S3:** One bucket holds 14 TB of legacy logs in Standard storage class. Last accessed: never.
- **EBS:** 38 unattached gp2 volumes totaling 4.2 TB. Oldest snapshot dates from 2022.
- **NAT Gateway:** Single NAT in `us-east-1a`. Lambda functions in private subnets call S3 through it instead of via a VPC endpoint.
- **CloudWatch Logs:** No retention policy set on most log groups — default infinite retention.
- **Untagged spend:** $1,800 nobody can attribute to a team.

## Tasks

1. **Identify the top 5 sources of waste.** For each, write one sentence on *why* it's waste.
2. **Pick the 3 optimizations you would do first.** Justify by expected impact and effort.
3. **Estimate annual savings** for your top three (rough order of magnitude is fine).
4. **Tagging:** propose one rule that would prevent the $1,800 of untagged spend going forward.

## Discussion Prompts

- Which fixes are one-time vs. ongoing?
- Which require engineering work vs. a finance/procurement decision (Savings Plans, RIs)?
- How would you avoid backsliding three months from now?

## Reference — One Possible Set of Findings

> Don't peek until you've made your own list.

1. Right-size or consolidate the eight underutilized `m5.2xlarge` instances → likely 50–70% EC2 reduction on those nodes.
2. Buy a 1-year Compute Savings Plan covering the steady-state EC2 baseline → ~25–30% on covered usage.
3. Schedule dev/staging RDS clusters off nights and weekends (or stop them) → ~60% on those clusters.
4. Move 14 TB of cold S3 logs to Glacier Instant Retrieval or Glacier Deep Archive → ~80–95% on that storage.
5. Delete the 38 unattached EBS volumes and old snapshots after owner sign-off.
6. Add an S3 Gateway VPC endpoint so Lambda → S3 traffic stops paying the NAT data-processing charge.
7. Apply CloudWatch Logs retention (e.g., 30 days for dev, 90 days for prod).
8. Enforce required tags (`env`, `owner`, `cost-center`) via an SCP or AWS Config rule.
