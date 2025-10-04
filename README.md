# GHZ under Z-type dephasing with Qiskit Aer

## Overview
This project is a small, reproducible study of how a 4-qubit GHZ state loses coherence under idle-only Z-type dephasing. I build the GHZ state once, insert explicit wait layers (identity gates with barriers so waits are preserved), attach a phase-damping noise channel to the identity operation, and track fidelity to the ideal GHZ state as circuit depth increases. Added a “repeats” parameter (extra idle ticks per layer) and confirms that a Z-only “echo” is neutral under memoryless dephasing.

## Why this is useful
A GHZ state concentrates quantum coherence in one off-diagonal element between the all-zeros and all-ones basis states. Pure dephasing shrinks exactly that term. By keeping noise on `id` only, the decay can be interpreted cleanly as “loss during waiting,” without conflating it with gate noise. 


## How I run it
1. Create a Python 3.11 environment with NumPy, Matplotlib, Qiskit, and Qiskit-Aer.
2. Open the notebook in Jupyter.
3. Run cells top to bottom.


## Modeling choices
- Noise: phase damping (Z-type, memoryless) attached to the `id` gate only
- Circuit: GHZ prepared once (H on q0; CNOT chain to entangle the register)
- Wait layers: identity on every qubit plus `barrier()` to avoid transpiler removal
- Simulator: density-matrix backend so Kraus channels are applied exactly
- Keep `z/rz` noise-free to keep echo comparisons fair

## Metrics reported
- Fidelity to the ideal 4-qubit GHZ vs depth

## Key results so far
- Fidelity decays monotonically with the number of idle ticks; increasing the `repeats` parameter steepens the decay.
- A Z-only “echo” is neutral under memoryless dephasing (Z commutes with Z-type noise; no coherent phase to refocus).


## License
MIT
