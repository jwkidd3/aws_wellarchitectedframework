# AWS Well-Architected Best Practices Workshop

A 1-day, introductory-level, **lab-heavy** workshop covering the six pillars of the AWS Well-Architected Framework. Every pillar has its own hands-on lab plus a capstone Well-Architected Review.

## Audience

Engineers, architects, and tech leads with basic AWS familiarity who want a structured way to evaluate and improve their workloads.

## Format

- Eight tight Reveal.js decks (3–5 slides each) — open the `.html` files in any browser
- **Seven paper-based labs** — no AWS account required
- About 60% of class time is hands-on

## Day Schedule

| Time          | Module / Lab                                          | Link                                                                   |
| ------------- | ----------------------------------------------------- | ---------------------------------------------------------------------- |
| 09:00 – 09:20 | 1. Introduction &amp; Framework Overview              | [01-introduction.html](presentations/01-introduction.html)             |
| 09:20 – 09:40 | 2. Operational Excellence (teaching)                  | [02-operational-excellence.html](presentations/02-operational-excellence.html) |
| 09:40 – 10:05 | **Lab 1 — Runbook Authoring**                         | [labs/lab1-runbook-authoring.md](labs/lab1-runbook-authoring.md)       |
| 10:05 – 10:20 | *Break*                                               |                                                                        |
| 10:20 – 10:40 | 3. Security (teaching)                                | [03-security.html](presentations/03-security.html)                     |
| 10:40 – 11:10 | **Lab 2 — IAM Least Privilege Review**                | [labs/lab2-iam-least-privilege.md](labs/lab2-iam-least-privilege.md)   |
| 11:10 – 11:30 | 4. Reliability (teaching)                             | [04-reliability.html](presentations/04-reliability.html)               |
| 11:30 – 11:55 | **Lab 3 — DR Pattern Selection**                      | [labs/lab3-dr-pattern-selection.md](labs/lab3-dr-pattern-selection.md) |
| 11:55 – 12:55 | *Lunch*                                               |                                                                        |
| 12:55 – 13:15 | 5. Performance Efficiency (teaching)                  | [05-performance-efficiency.html](presentations/05-performance-efficiency.html) |
| 13:15 – 13:40 | **Lab 4 — Compute Selection**                         | [labs/lab4-compute-selection.md](labs/lab4-compute-selection.md)       |
| 13:40 – 14:00 | 6. Cost Optimization (teaching)                       | [06-cost-optimization.html](presentations/06-cost-optimization.html)   |
| 14:00 – 14:30 | **Lab 5 — Cost Allocation Analysis**                  | [labs/lab5-cost-allocation-analysis.md](labs/lab5-cost-allocation-analysis.md) |
| 14:30 – 14:45 | *Break*                                               |                                                                        |
| 14:45 – 15:00 | 7. Sustainability (teaching)                          | [07-sustainability.html](presentations/07-sustainability.html)         |
| 15:00 – 15:20 | **Lab 6 — Sustainability Quick Wins**                 | [labs/lab6-sustainability-quick-wins.md](labs/lab6-sustainability-quick-wins.md) |
| 15:20 – 15:40 | 8. Practical Application &amp; Wrap-Up                | [08-practical-application.html](presentations/08-practical-application.html) |
| 15:40 – 16:25 | **Lab 7 — Mini Well-Architected Review (Capstone)**   | [labs/lab7-mini-wa-review.md](labs/lab7-mini-wa-review.md)             |
| 16:25 – 17:00 | Capstone debrief &amp; Q &amp; A                      |                                                                        |

## Repository Layout

```
.
├── README.md
├── presentations/
│   ├── 01-introduction.html
│   ├── 02-operational-excellence.html
│   ├── 03-security.html
│   ├── 04-reliability.html
│   ├── 05-performance-efficiency.html
│   ├── 06-cost-optimization.html
│   ├── 07-sustainability.html
│   └── 08-practical-application.html
└── labs/
    ├── lab1-runbook-authoring.md
    ├── lab2-iam-least-privilege.md
    ├── lab3-dr-pattern-selection.md
    ├── lab4-compute-selection.md
    ├── lab5-cost-allocation-analysis.md
    ├── lab6-sustainability-quick-wins.md
    └── lab7-mini-wa-review.md
```

## Running the Decks

Each presentation is a single self-contained HTML file using Reveal.js loaded from a CDN. Open it directly in a browser — no build step.

```
open presentations/01-introduction.html
```

Navigation: arrow keys, `f` for fullscreen, `s` for speaker view, `?` for help.

## Learning Objectives

By the end of the day participants will be able to:

1. Explain the purpose and structure of the AWS Well-Architected Framework
2. Describe the design principles and key services of each of the six pillars
3. Author a runbook fit for a 3 AM incident
4. Spot common least-privilege violations in IAM policies
5. Pick an appropriate DR pattern for a given RTO/RPO
6. Choose between Lambda, containers, and EC2 for a workload
7. Read a cost report and propose prioritized optimizations
8. Identify sustainability improvements that also help cost or performance
9. Run a Well-Architected Review and turn its findings into a remediation roadmap
