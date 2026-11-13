# 🛡️ Deep Learning for Intrusion Detection
### Individual Research & Critical Analysis | 3D-IDS and KAIROS

![Research](https://img.shields.io/badge/Type-Research_%26_Critical_Analysis-635bff) ![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-146c94) ![Deep Learning](https://img.shields.io/badge/Focus-Deep_Learning-0f766e) ![Year](https://img.shields.io/badge/Year-2026-475569)

**Research by Fairouz Abdulrahman Hamed Mousa**  
BSc (Hons) Computer Science (Cyber Security) · Asia Pacific University of Technology & Innovation · 2026

> **Contribution statement:** This repository documents **my individual research and critical analysis** from a broader group assignment in *Deep Learning for Intrusion Detection*. The wider report and the DCNNBiLSTM implementation were collaborative work; I do **not** claim sole authorship or implementation of those systems. The 3D-IDS and KAIROS systems described below were developed by their respective research authors, not by me.

---

## Overview

My research examined two graph-based approaches to intrusion detection: **3D-IDS**, which addresses overlapping network traffic representations, and **KAIROS**, which detects and investigates suspicious system activity using provenance graphs. I evaluated their research goals, architectural techniques, reported results, operational strengths, and limitations for real-world security environments.

![Research focus diagram](assets/research-overview.svg)

## Research questions

- How can graph-based deep learning improve detection of complex and previously unseen attacks?
- What is the difference between network-flow intrusion detection and host-level provenance analysis?
- How well do published benchmark results translate to practical deployment?
- What limitations remain around concept drift, resource requirements, false positives, and explainability?

## 1. 3D-IDS — Doubly Disentangled Dynamic Intrusion Detection

**Research studied:** Qiu et al. (2023), *3D-IDS*.

### Problem and approach

Network intrusion detectors can struggle when features from different attack categories overlap. 3D-IDS seeks to disentangle these distributions at statistical and representational levels, then learn spatial–temporal traffic relationships through graph-based diffusion.

| Component | Role described in the research |
|---|---|
| Statistical disentanglement | Uses non-parametric mutual information optimization formulated as an SMT problem |
| Representational disentanglement | Uses GRU-based memory and near-orthogonality regularization |
| Dynamic graph diffusion | Learns spatial–temporal traffic patterns using nonlinear diffusion |
| Two-stage classification | Supports binary and multiclass attack detection |

![3D-IDS research analysis](assets/3d-ids-analysis.svg)

### Reported findings

- **98.24% F1** on CIC-BoT-IoT, reported as 4.80 percentage points above the earlier record.
- **33.65% mean F1** for unknown-attack detection in the reported comparison.
- Removing the graph diffusion component was reported to reduce **AUC by 18.33 points**.

*These figures are results reported in the reviewed study and summarized in my assignment; they are not experiments I independently reproduced.*

### My critical evaluation

The explicit treatment of entangled attack representations is a notable methodological strength. However, evaluation across IoT-oriented benchmarks leaves broader enterprise and cloud generalization uncertain. The computational requirements, including an RTX 3090-class evaluation environment, raise questions about constrained deployment. Unknown-attack performance remains limited, and the explainability evidence is narrower than would be desirable for operational adoption.

## 2. KAIROS — Practical Intrusion Detection and Investigation with Whole-System Provenance

**Research studied:** Cheng et al. (2024), *KAIROS*.

### Problem and approach

Advanced persistent threats can blend into ordinary system activity. KAIROS analyzes streaming system audit events as a dynamic provenance graph, learns normal behavior, flags anomalous events, and reconstructs compact attack summaries to support investigation.

| Component | Role described in the research |
|---|---|
| System audit provenance | Represents process, file, and related activity as graph events |
| Temporal Graph Network | Learns changing entity and event representations |
| Event prediction | Uses an MLP decoder and reconstruction error to flag anomalies |
| Attack reconstruction | Summarizes anomalous events into investigator-readable graphs |

![KAIROS research analysis](assets/kairos-analysis.svg)

### Reported findings

- **100% recall** across the evaluated DARPA benchmark datasets, as summarized in the report.
- **3.27% false-positive rate**, compared with **16.82%** for the cited MLP baseline.
- Approximately **11,000 events per second** processed.
- In one E3-THEIA example, the investigation scope fell from **3.4 million edges to 31**, described as a reduction of up to **109,469×**.

*These are published benchmark results, not my own experimental measurements.*

### My critical evaluation

Training on benign events reduces dependence on labeled attacks, and compact attack reconstruction is valuable for security analysts. Nevertheless, benchmark campaigns may not fully represent adaptive real-world adversaries. A fixed learned baseline can degrade under concept drift, while legitimate administrative tools used maliciously may produce behavior difficult to distinguish from routine operations.

## Comparative perspective

| Dimension | 3D-IDS | KAIROS |
|---|---|---|
| Primary data | Network/IoT traffic | Host-level system audit events |
| Graph modeling | Dynamic graph diffusion and disentanglement | Temporal provenance graphs |
| Main objective | Improve separation and classification of attack traffic | Detect anomalies and reconstruct attack activity |
| Practical challenge | Compute cost and unknown-attack generalization | Drift and stealthy legitimate-tool activity |
| Investigation value | Detection-oriented classification | Detection plus summarized causal context |

**Key takeaway:** Strong benchmark performance alone does not establish deployment readiness. Resource constraints, data distribution changes, explainability, and investigation workload all matter.

## Research scope and integrity

This is an **individual research portfolio**, not a runnable IDS implementation. It does not include training scripts, model weights, datasets, or code from the group's implementation. The diagrams are original explanatory summaries of the literature, not reproductions of the original research figures.

## Repository structure

```text
Deep-Learning-Intrusion-Detection-Research/
├── README.md
├── assets/
│   ├── research-overview.svg
│   ├── 3d-ids-analysis.svg
│   └── kairos-analysis.svg
└── docs/
    └── CONTRIBUTION_AND_SOURCES.md
```

## References and attribution

- Qiu et al. (2023). *3D-IDS — Doubly Disentangled Dynamic Intrusion Detection*.
- Cheng et al. (2024). *KAIROS: Practical Intrusion Detection and Investigation with Whole-System Provenance*.

For complete bibliographic information, refer to the original papers and the reference list of the academic report. The research findings belong to the original authors.

---

**Author:** Fairouz Abdulrahman Hamed Mousa  
**Module:** CT115-3-3-DLI · Deep Learning for Intrusion Detection  
**Institution:** Asia Pacific University of Technology & Innovation  
**Year:** 2026

*Understanding the strengths and operational limitations of graph-based intrusion detection.*
