# Evaluation Plan

## Data & Preprocessing
- Use the challenge’s synthetic PK/PD dataset once provided.
- Compute summary features per patient: AUC, Cmax, t½ (approx), Tmax; join with available covariates.
- Optionally embed short windows of the time‑course for sequence models.

## Splits & Leakage Avoidance
- Patient‑level k‑fold cross‑validation (k=5); no patient appears in both train and test.
- Covariate‑aware stratification where possible.
- All preprocessing fit **within** each training fold; validate via checksums.

## Learning Curves
- Train sizes N ∈ {4, 8, 16, 32} per fold to study low‑N behavior.

## Models
- Baseline: population PK/PD (two‑compartment + Emax) as clinical reference.
- Quantum kernels: QSVM/QKRR on shallow feature maps (depth 1–2).
- Tensor networks: MPS regressors with small bond dimensions.

## Metrics & Uncertainty
- Regression: RMSE/MAE; (if applicable) Classification: AUC.
- 95% CIs via 200× bootstrap; report variance across seeds for stochastic models.

## Calibration
- Reliability curves + Expected Calibration Error (ECE) for probabilistic outputs.

## Reporting
- Tables with mean ± CI; ablations (qubits, depth, bond dim, features).
- “What worked / what didn’t” section summarizing findings and limitations.
