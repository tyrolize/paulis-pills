# Computational Resource Estimate

- **Baseline (population PK/PD):** CPU 8–16 vCPU, 8–12 GB RAM; ≈ 1–2 h
- **Quantum kernels (8–12 qubits, depth 1–2):** CPU 8–16 vCPU, 16–32 GB RAM; 5×CV @ 1024 shots ≈ 2–4 h
- **Tensor networks (MPS):** CPU 8–16 vCPU, 8–16 GB RAM; ≈ 1–2 h
- **Optional GPU (deep surrogates only):** 1× NVIDIA L4/A100; ≈ 2–4 h

**Notes**
- Use fixed seeds and deterministic settings where possible.
- Provide config files and exact splits to ensure reproducibility.
