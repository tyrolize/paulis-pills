# Risk Assessment & Mitigation

| Risk | Impact | Mitigation |
|------|--------|------------|
| Overfitting in low‑N | Misleading gains | Patient‑level splits, learning curves, calibration & CI reporting |
| Runtime/memory spikes | Missed deadlines | Cap qubits/depth & bond dims; provide smaller configs |
| Dataset mismatch | Models underperform | Expand features; include classical benchmarks; document negatives |
| Reproducibility issues | Non‑evaluable | Seed control, config‑driven runs, commit split manifests |
