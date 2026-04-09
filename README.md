# AWS Well-Architected Best Practices Workshop

A 1-day, introductory-level, **lab-heavy** workshop covering the six pillars of the AWS Well-Architected Framework. Every pillar has its own hands-on lab plus a capstone Well-Architected Review.

## Audience

Engineers, architects, and tech leads with basic AWS familiarity who want a structured way to evaluate and improve their workloads.

## Before the Workshop

Students should read [PRE-READ.md](PRE-READ.md) a few days before class — it covers the six pillars, prerequisites, what to bring, and links to the official [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/).

## Format

- Eight tight Reveal.js teaching decks (3–5 slides each)
- **Seven Reveal.js lab decks** — paper-based analysis exercises paired with short, read-only AWS Console navigation
- Students log into a shared class AWS account for navigation only — no creates or edits
- All material is single-file HTML — open in any browser, no build step
- About 60% of class time is hands-on

## Day Schedule

Class runs **09:00 – 16:00**. Instructor calls breaks as needed.

| Time          | Module / Lab                                          | Link                                                                   |
| ------------- | ----------------------------------------------------- | ---------------------------------------------------------------------- |
| 09:00 – 09:20 | 1. Introduction &amp; Framework Overview              | [01-introduction.html](presentations/01-introduction.html)             |
| 09:20 – 09:40 | 2. Operational Excellence                             | [02-operational-excellence.html](presentations/02-operational-excellence.html) |
| 09:40 – 10:10 | **Lab 1 — Runbook Authoring** (incl. AWS login)       | [lab1-runbook-authoring.html](labs/lab1-runbook-authoring.html)        |
| 10:10 – 10:30 | 3. Security                                           | [03-security.html](presentations/03-security.html)                     |
| 10:30 – 11:00 | **Lab 2 — IAM Least Privilege Review**                | [lab2-iam-least-privilege.html](labs/lab2-iam-least-privilege.html)    |
| 11:00 – 11:20 | 4. Reliability                                        | [04-reliability.html](presentations/04-reliability.html)               |
| 11:20 – 11:45 | **Lab 3 — DR Pattern Selection**                      | [lab3-dr-pattern-selection.html](labs/lab3-dr-pattern-selection.html)  |
| 11:45 – 12:45 | *Lunch*                                               |                                                                        |
| 12:45 – 13:05 | 5. Performance Efficiency                             | [05-performance-efficiency.html](presentations/05-performance-efficiency.html) |
| 13:05 – 13:30 | **Lab 4 — Compute Selection**                         | [lab4-compute-selection.html](labs/lab4-compute-selection.html)        |
| 13:30 – 13:50 | 6. Cost Optimization                                  | [06-cost-optimization.html](presentations/06-cost-optimization.html)   |
| 13:50 – 14:20 | **Lab 5 — Cost Allocation Analysis**                  | [lab5-cost-allocation-analysis.html](labs/lab5-cost-allocation-analysis.html) |
| 14:20 – 14:35 | 7. Sustainability                                     | [07-sustainability.html](presentations/07-sustainability.html)         |
| 14:35 – 14:55 | **Lab 6 — Sustainability Quick Wins**                 | [lab6-sustainability-quick-wins.html](labs/lab6-sustainability-quick-wins.html) |
| 14:55 – 15:15 | 8. Practical Application &amp; Wrap-Up                | [08-practical-application.html](presentations/08-practical-application.html) |
| 15:15 – 16:00 | **Lab 7 — Mini Well-Architected Review (Capstone)**   | [lab7-mini-wa-review.html](labs/lab7-mini-wa-review.html)              |

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
    ├── lab1-runbook-authoring.html
    ├── lab2-iam-least-privilege.html
    ├── lab3-dr-pattern-selection.html
    ├── lab4-compute-selection.html
    ├── lab5-cost-allocation-analysis.html
    ├── lab6-sustainability-quick-wins.html
    └── lab7-mini-wa-review.html
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
