# Lab 4 — Compute Selection

**Duration:** ~25 minutes
**Pillar:** Performance Efficiency

## Objective

For three workloads, pick a compute option (Lambda, Fargate/ECS/EKS containers, or EC2) and justify it against traffic shape, runtime constraints, and operational cost. There are no single right answers — defend your reasoning.

## Decision Aids

- **Lambda** shines for: short bursty work, event-driven, unpredictable load, minimal ops
- **Containers** shine for: long-running services, complex runtimes, portability, steady or predictable burst load
- **EC2** shines for: specialized hardware, GPU, very long jobs, software with licensing tied to a host, or when you genuinely need OS-level control

## Workload A — Image Thumbnail Generator

- Triggered when a user uploads a photo to S3
- ~50,000 events/day, very bursty (spikes around evenings)
- Each invocation runs 2–8 seconds, mostly CPU
- Must scale instantly; idle most of the night

## Workload B — Internal Analytics API

- Steady ~200 requests/second, 24×7
- Custom Python service with native dependencies (NumPy, pandas, a C library)
- Average request 150 ms; long tail of 2-second requests
- Team has Kubernetes experience and existing CI for container images

## Workload C — Genomic Sequence Aligner

- Batch job, runs for 6–12 hours per execution
- Requires 192 GB RAM and a specific GPU instance family
- Runs 3–4 times per week, scheduled in advance
- Cost-sensitive; interruption is recoverable from a checkpoint

## Tasks

For each workload (A, B, C):

1. **Compute choice** — pick Lambda, Containers, or EC2
2. **Specifics** — instance type / Lambda memory / Fargate vCPU as relevant
3. **Why this and not the others** — one sentence per rejected option
4. **Pillar interactions** — does your choice change Cost, Reliability, or Sustainability outcomes? How?

## Discussion

- Which workload had the most divided answers around the room?
- For Workload C, would Spot instances be appropriate? What about Workload A?
- For Workload B, what would have to change to make Lambda the right answer?
