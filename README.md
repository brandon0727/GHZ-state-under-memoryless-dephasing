# GHZ under Z-type dephasing with Qiskit Aer

## Overview
This project is a small, reproducible study of how a GHZ state loses coherence under idle-only Z-type dephasing. I build the GHZ state, insert explicit wait layers (identity gates with barriers so waits are preserved), attach a phase-damping noise channel to the identity operation, and track fidelity and log-negativity to the ideal GHZ state as circuit depth increases. Added a “repeats” parameter (extra idle ticks per layer) and confirms that a Z-only “echo” is neutral under memoryless dephasing.

## How I run it
1. Create a Python 3.11 environment with NumPy, Matplotlib, Qiskit, and Qiskit-Aer.
2. Open the notebook in Jupyter.
3. Run cells top to bottom.

## Modeling choices
- Noise: phase damping (Z-type, memoryless) attached to the `id` gate only
- Circuit: GHZ prepared  (H on q0; CNOT chain)
- Wait layers: identity on every qubit plus `barrier()` to avoid transpiler removal
- Simulator: density-matrix backend so Kraus channels are applied exactly

## Metrics reported
- Fidelity to the ideal 4-qubit GHZ vs depth
- Log-negativity

## License
MIT

## References

[1] M. A. Nielsen and I. L. Chuang, *Quantum Computation and Quantum Information*,  
Cambridge University Press (2010).

[2] A. Peres, “Separability Criterion for Density Matrices,”  
*Physical Review Letters* **77**, 1413 (1996).

[3] M. Horodecki, P. Horodecki, and R. Horodecki,  
“Separability of Mixed States: Necessary and Sufficient Conditions,”  
*Physics Letters A* **223**, 1–8 (1996).

[4] G. Vidal and R. F. Werner, “Computable Measure of Entanglement,”  
*Physical Review A* **65**, 032314 (2002).

[5] Qiskit Aer Documentation, *Noise Models and Density-Matrix Simulation*,  
Available at: https://qiskit.org/ecosystem/aer/
