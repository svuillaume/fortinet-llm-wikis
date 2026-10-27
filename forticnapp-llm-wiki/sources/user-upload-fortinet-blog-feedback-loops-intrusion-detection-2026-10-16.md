---
title: "How Feedback Loops and Machine Learning Power High-Precision Intrusion Detection in Lacework FortiCNAPP (Fortinet blog, David Adamson)"
path: chat upload 781cf743-attachment.txt, 2026-10-16 (web clipping; original location on disk not stated)
url: https://www.fortinet.com/blog/business-and-technology/how-feedback-loops-and-machine-learning-power-high-precision-intrusion-detection
inline: true
topic: demos-blogs-field
tags: [composite-alerts, false-positive, true-positive, false-negative, feedback-loop, machine-learning, precision, recall, release-gate]
updated: 2026-10-16
size: 10153
sha1: 61c1a95eafc9
status: current
---

**Source:** a Markdown web clipping of a Fortinet blog by David Adamson, uploaded in chat and ingested with `llm-wiki-ingest`. Clipping created 2026-10-16. The `published: 2001-08-01` field in its frontmatter is clearly wrong; the real publication date is not stated. The page was not re-opened during ingest. Figures 1-3 are referenced in the text but the images were not extracted.

## Summary

- **Composite Alerts** score many signals together instead of firing on one rule or IOC. Signal families: threat behaviors (access-control bypass, privilege escalation), IOCs (curated feeds of malicious IPs, domains, hashes) and anomalies (global, per-institution, per-user/system/workload). Inputs may be rules, anomaly models or behavioral baselines, Boolean or numeric, all normalized into the scoring engine.
- **Three signal roles:** decisive (alert on its own), combinatorial (predictive only alongside others), contextual (no effect on detection, forensic detail after an alert).
- **User feedback:** when closing a Composite Alert the user can label it **true positive** (confirmed threat or pen test) or **false positive** (benign behavior misclassified), and can report **false negatives** (missed intrusions). Labels, with a snapshot of the signals present, join the training corpus.
- **Training:** the corpus trains the Composite Alert scoring models, which are retrained as feedback arrives. Signals are Boolean or numeric only, so training is described as anonymized and no customer-specific content enters the models.
- **Signal design loop:** model output shows which signals are predictive or noisy; weak signals are refined, demoted or removed, and new signals are benchmarked on historical data before deployment. Some signals that looked predictive were deprioritized; some peripheral ones proved strong in context.
- **Testing:** nightly automation runs each candidate build on (1) labeled intrusion scenarios (synthetic, red-team, customer-labeled) to measure precision = TP/(TP+FP) and recall = TP/(TP+FN), and (2) recent unlabeled customer telemetry to measure overall alert rate and catch alert-flood regressions.
- **Release gate:** precision, recall and alert-volume thresholds are formal release criteria; a build must improve or at least not regress on all primary metrics.

No numeric results (precision, recall, false-positive rates) are given in this post.
