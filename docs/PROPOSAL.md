# Pauli’s Pills — Phase 1 Proposal

## 1) Overview & Objectives
- Develop and evaluate a **PK/PD dose‑selection** pipeline using **quantum or quantum‑inspired** methods alongside strong classical baselines.
- Report **clear generalization behavior under small‑N** (few‑patient) settings and provide a **transparent resource estimate** for compute.
- Deliver an open, reproducible repository (code under Apache‑2.0/MIT; docs under CC BY 4.0).

## 2) Problem Understanding & Context
Dose finding in early studies is statistically fragile. The challenge provides a **synthetic clinical dataset**; the aim is to design methods that are **technically feasible** and **informative** under limited data. We will compare quantum kernel methods and tensor‑network regressors to a **population PK/PD** baseline to understand when and how they help.

## 3) Proposed Approach
**Data features.** PK/PD summaries (AUC, Cmax, t½, Tmax) and selected covariates; optional short time‑window embeddings.  
**Baselines.** Population PK/PD (two‑compartment + Emax) as a clinical reference; simple classical kernels/GPs.  
**Quantum/Quantum‑inspired.** Shallow **quantum kernels** (QSVM/QKRR via simulator) and compact **tensor‑network** regressors (MPS).  
**Dose suggestion.** Bayesian optimization atop the best surrogate with simple safety constraints.

## 4) Technical Feasibility
- **Quantum kernels:** limit to ~8–12 qubits and depth 1–2; run on simulators with modest CPU.  
- **Tensor networks:** use small bond dimensions.  
- **Baselines:** standard PK/PD modeling toolchain.  
These choices keep runtime and memory modest and ensure reproducibility on commodity hardware.

## 5) Innovativeness & State of the Art
- Contrast **quantum kernels** and **tensor networks** against a clinical baseline under **few‑sample** conditions.  
- Emphasize **calibration/uncertainty** and “what worked / what didn’t,” not just point accuracy.  
- Provide a **clean ablation plan** for qubits/depth and bond dimension.

## 6) Evaluation Plan (summary)
- **Splits:** patient‑level k‑fold (k=5) with covariate‑aware stratification.  
- **Learning curves:** N ∈ \{4, 8, 16, 32\} to study low‑N behavior.  
- **Metrics:** regression (RMSE/MAE) and, where applicable, classification (AUC); report **95% CIs** via bootstrap and **seed variance** for stochastic methods.  
- **Calibration:** reliability curves/ECE.  
- Full detail in `docs/EVALUATION_PLAN.md`.

## 7) Computational Resource Estimate (summary)
- **PK/PD baseline:** CPU 8–16 vCPU, 8–12 GB RAM, ~1–2 h  
- **Quantum kernels (8–12 qubits, shallow):** CPU 8–16 vCPU, 16–32 GB RAM, 5×CV @ 1024 shots ≈ 2–4 h  
- **Tensor networks (MPS):** CPU 8–16 vCPU, 8–16 GB RAM, ~1–2 h  
- **Optional GPU:** 1× NVIDIA L4/A100 for ~2–4 h (deep surrogates only)  
See `docs/RESOURCE_ESTIMATE.md`.

## 8) Work Plan & Milestones
**M1. Repo & data interface (Phase 1)** — finalize docs, config stubs, and evaluation plan.  
**M2. Baseline & features** — implement PK/PD baseline and feature engineering; sanity checks.  
**M3. Quantum/tensor models** — implement QSVM/QKRR on simulator and MPS; small learning‑curve experiments.  
**M4. Dose‑selection demo** — simple BO on learned surrogates; summarize risk/benefit.  
**M5. Reporting** — finalize tables, ablations, calibration plots, and narrative.

## 9) Risks & Mitigations
- **Low‑N overfitting:** strict patient‑level splits, calibration reporting, and CI bootstrap.  
- **Runtime/memory spikes:** cap qubit count/depth and bond dimension; provide config to scale down.  
- **Unclear benefit over classical:** document negative results; broaden features/baselines as needed.

## 10) Team & Roles (concise)
- **Artemiy Burov (FHNW)** — quantum algorithms & encodings; project lead; contact: artemiy.burov@fhnw.ch  
- **Leena Anthony (FHNW)** — QML validation & evaluation protocols  
- **Johannes Mosbacher (FHNW)** — PK/PD guidance  
- **Martin Kuentz (FHNW)** — dosage forms & clinical relevance  
- **Abdullah Kahraman (FHNW/SIB)** — data science, reproducibility  
- **Nicolas Piro (Sony Advanced Visual Sensing AG (Zurich, Switzerland))** — ML

## 11) Openness & Licensing
- **Code:** Apache‑2.0 or MIT (repo already set to Apache‑2.0).  
- **Docs/report:** CC BY 4.0.  
- **No proprietary or confidential assets** will be included.

## 12) Deliverables (Phase 1)
1. Project page (challenge repo) with title/front‑matter, summary, and links.  
2. This proposal and the evaluation plan, resource estimate, and work plan documents.  
3. Repository README with run instructions and license (already present).  
4. (Optional) short video + social post.
