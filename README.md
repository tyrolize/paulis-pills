# Pauli’s Pills — Validating Few‑Sample Quantum ML for PK/PD Dose Selection

**Team:** pauli's pills  
**Official participants (Team Leads):** Leena Anthony (FHNW), Artemiy Burov (FHNW)  
**License:** Apache-2.0 (code); CC BY 4.0 (docs/report)

## Summary
We adapt **few‑sample QML generalization validation** (from medical imaging) to **PK/PD**: we define rigorous low‑N protocols (patient‑level splits, small learning curves, calibration/variance) and compare **quantum kernels (QSVM/QKRR)** and compact **tensor‑network** baselines to a clinical **population PK/PD** reference. Physics‑informed encodings (AUC, Cmax, t½, Tmax, covariates) keep circuits shallow and interpretable.

## Methods
- **Generalization protocol:** few‑shot k‑folds with patient‑level separation; covariate‑aware splits; robust CIs & calibration.
- **Baselines:** `nlmixr2/rxode2` two‑compartment + Emax; simple classical kernels/GPs.
- **Quantum kernels:** Pauli/ZZ maps (depth 1–2), QSVM/QKRR on simulator; report variance across seeds.
- **Tensor networks (MPS):** compact sequence regression; compare on identical features.
- **Dose suggestion:** Bayesian optimization on the best surrogate under safety constraints.

## Reproducibility
- Split manifests committed; one‑command runners in `src/`; configs checked‑in.
- Results tables include **what worked / what didn’t**, focusing on **low‑N stability**.

## Computational resources (Phase 1)
- Population PK/PD: CPU 8–16 vCPU, 8–12 GB RAM, ~1–2 h
- Quantum kernels (8–12 qubits, shallow): CPU 8–16 vCPU, 16–32 GB RAM, 5×CV @ 1024 shots ≈ 2–4 h
- MPS: CPU 8–16 vCPU, 8–16 GB RAM, ~1–2 h
- Optional GPU (deep surrogates only): 1× L4/A100 for ~2–4 h

## Team (light roles)
- **Leena Anthony (FHNW)** — QML **generalization** on small medical datasets; protocol & evaluation lead.  
- **Artemiy Burov (FHNW)** — quantum algorithms & **Hamiltonian simulation**; encodings & circuits (e.g., arXiv:2404.17548).  
- **Johannes Mosbacher (FHNW)** — PK/PD & biomarkers.  
- **Martin Kuentz (FHNW)** — dosage forms & clinical relevance.  
- **Abdullah Kahraman (FHNW/SIB)** — data science & reproducibility.  
- **Nicolas Piro (Sony Advanced Visual Sensing AG (Zurich, Switzerland))** — quantum optics/ML perspective.
