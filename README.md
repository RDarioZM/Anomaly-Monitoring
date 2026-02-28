
---
# Laundromat Telemetry Analytics — Anomaly Monitoring

**Status:** WIP (validated offline; integration into commercial POS pending)  
**Scope:** Analytics + ML/monitoring layer only (commercial POS is private)  
**Goal:** Infer machine cycles from electrical telemetry to detect operational anomalies.

---

## Overview
This repository contains the **telemetry analytics and anomaly monitoring layer** for a laundromat POS ecosystem (the POS product is commercial and remains private).  
It focuses on:
- Prototype **anomaly monitoring** (robust baselines + drift/SPC)

---

## What you’ll find here
- Signal processing + cycle segmentation
- Cycle-level feature extraction (duration, energy, peaks)
- Monitoring prototypes (cohorts, thresholds, drift checks)
- Batch/offline scripts and report outputs

---

## Data
**Inputs (expected):**
- Telemetry sampled every 5–10s (current/power/energy)
- Optional machine metadata (model/type)

**Privacy:** No customer PII is stored. Examples use anonymized IDs and/or synthetic telemetry.

---

## Approach (high level)
### Cycle detection
- Start/end detection via thresholds + hysteresis
- Extract cycle-level features (duration, energy, peak power)

### Monitoring (prototype)
- Robust baselines (median/IQR, percentiles) per machine/cohort
- Drift checks using SPC/control charts on key features

---

## Current results (placeholder)
> Replace with plots/logs you can support.
- Offline cycle segmentation validated across multiple machine behaviors.
- Monitoring runs as an external workflow; POS integration is pending.

---

## Repo structure
```text
.
├─ data/                      # sample telemetry (synthetic or small)
├─ notebooks/                 # EDA + signal experiments
├─ src/
│  ├─ ingest/                 # parsers/loaders
│  ├─ signals/                # filtering + segmentation + features
│  ├─ reconcile/              # matching logic
│  ├─ anomaly/                # baselines + drift/SPC
│  └─ utils/
├─ reports/                   # figures, KPI summaries, example briefs
├─ requirements.txt
└─ README.md
