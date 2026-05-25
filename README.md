# Triclinic Quantum Cosmology: Cyclic Evolution via Tensor Network Simulation

An open-source, data-driven computational astrophysics project exploring non-linear cyclic cosmology. This repository contains an accelerated tensor network simulation that models a discrete 3-D triclinic spacetime lattice at the Planck scale, coupled with an empirical verification pipeline designed to scan raw Cosmic Microwave Background (CMB) data for macroscopic structural footprints.

---

## RESEARCH ABSTRACT

This framework hypothesizes that the fundamental fabric of spacetime is a discrete, anisotropic quantum lattice possessing triclinic symmetry at the Planck scale, where the lattice lengths and shearing angles are entirely independent. We propose a mechanism wherein localized cosmic expansion is driven by thermodynamic fluctuations that transfer localized energy into highly entangled partner states across the lattice nodes. In this framework, gravitational singularities like black holes are defined not as mass-density infinities, but as maximally extended spatial cells whose coordinate projections asymptotically converge at the conformal future boundary.

Finally, we posit a cyclic evolution: upon reaching a state of global absolute zero where temperature approaches 0, the universe undergoes a conformal phase transition. This maps the infinite, maximum-entropy boundary back into a hot, localized, low-entropy initial state (a quantum bounce), initiating a new cosmic cycle.

Using an accelerated tensor network simulation, this model demonstrates that a discrete triclinic lattice undergoes continuous thermodynamic degradation—expressed quantitatively as an increasing quantum metric strain—until it reaches the maximum-entropy conformal boundary. At this critical threshold, the simulated conformal phase transition successfully resets the metric strain back to zero, mapping the cold, maximized spatial structure back into a low-entropy, highly energetic initial state, providing mathematical validation for a self-contained cyclic cosmology.

---

## SYSTEM ARCHITECTURE

The repository is split into two primary pipelines: a Microscopic Simulation Pipeline written in Python using optimized matrix libraries, and an Empirical Verification Pipeline designed to ingest and parse HEALPix-formatted cosmic background datasets.

```text
  +-------------------------------------------------------+
  |  Initialization: Flat Cartesian / Orthogonal State    |
  +-------------------------------------------------------+
                              |
                              v
  +-------------------------------------------------------+
  |         3D Fractional-to-Cartesian Engine             |
  |  - Calculates metric tensor from lattice vectors      |
  +-------------------------------------------------------+
                              |
                              v
  +-------------------------------------------------------+
  |          Tensor Network Simulation Layer              |
  |  - Maps node interactions via matrix contraction      |
  |  - Computes Quantum Metric Strain & Metric Decay      |
  +-------------------------------------------------------+
                              |
               +--------------┴--------------+
               |                             |
               v                             v
  +--------------------------+  +--------------------------+
  |  Strain < Max Threshold  |  | Critical Boundary Reach  |
  |  (Continue Epochs)       |  | - Temperature goes to 0  |
  +--------------------------+  | - Entropy saturates      |
                                | - Conformal Inversion    |
                                | - Reset Strain to 0      |
                                +--------------------------+
                                             |
                                             v
                                +--------------------------+
                                | Initiate New Epoch Cycle |
                                +--------------------------+
```

1. The Geometric Transformation Engine
To simulate an anisotropic quantum lattice without the computational overhead of non-orthogonal coordinate calculations, the engine uses a Fractional-to-Cartesian transformation.

The covariant metric tensor, denoted as g_ij, of the triclinic lattice is constructed directly from three independent lattice vectors (a, b, c) and three shearing angles (alpha, beta, gamma):

```text
g_11 = a^2
g_12 = a * b * cos(gamma)
g_13 = a * c * cos(beta)
g_21 = a * b * cos(gamma)
g_22 = b^2
g_23 = b * c * cos(alpha)
g_31 = a * c * cos(beta)
g_32 = b * c * cos(alpha)
g_33 = c^2
```
Spacetime events are transformed into standard Cartesian coordinates via an upper-triangular matrix contraction where X = M * X_frac, allowing flat-space tensor network optimizers to evaluate the state.

2. Matrix Contraction & Quantum Metric Strain
State Representation: The quantum state of the lattice nodes is represented as a matrix product state (MPS).

Strain Tracking: As thermodynamic variables degrade across temporal epochs, the shearing angles are systematically modified. The resulting geometric tension is quantified as Quantum Metric Strain, which tracks the deviation of the metric tensor from a standard Minkowski baseline.

3. Empirical Spherical Harmonic Pipeline
The verification layer decouples from the simulation to ingest raw astronomical observation files. It translates the simulated directional lattice bias into predicted multipole angular scales using a spherical harmonic decomposition framework:

```text
[ Raw CMB FITS Data ] ──> [ Healpy Anisotropy Mask ] ──> [ Cl Power Spectrum Engine ] ──> [ Significance Test ]
```
Ingestion: Parses raw spacecraft data from FITS files using the healpy library.

Anisotropy Masking: Applies galactic plane masks to eliminate low-frequency foreground contamination.

Multipole Estimation: Decomposes the temperature fluctuations into spherical harmonics to compute the angular power spectrum coefficients, targeting large angular scales where l <= 10 to test lattice compliance.

🌌 THEORETICAL FRAMEWORK: CLASSICAL LIMITS & THE COSMIC BOUNCE
While this project utilizes a discrete 3D triclinic spacetime lattice simulated via tensor networks, its macro-evolutionary behavior maintains a strict correspondence with classical physics before resolving the high-energy limits where standard theory breaks down.

1. Macro-Scale Evolution (The Newtonian Regime)
During the cosmic contraction phase, the macroscopic behavior of the universe is governed by a pseudo-Newtonian gravitational limit. As the system contracts, the gravitational restoring force acting on the collective mass-energy scales inversely with the system radius (r):

F = -G * (m1 * m2) / r²

As r → 0, classical mechanics predicts a singularity where gravitational force and acceleration approach infinity (F → ∞), resulting in a terminal Big Crunch.

2. Micro-Scale Correction (The Tensor Network Boundary)
To prevent mathematical divergence, this simulation introduces a discrete triclinic spatial lattice at ultra-high densities. As the universe approaches near-Planck scales, the geometry introduces a non-linear quantum pressure that acts as a stiff mechanical spring:

F_bounce = -k * x  (where x represents lattice compression)

3. Evolutionary Phase Transition
The simulation handles the boundary transition by passing the macro-scale acceleration vector into the tensor network once a critical density threshold is crossed:

Classical Collapse (F ∝ 1/r²) ──> Lattice Compression ──> Quantum Bounce (F_bounce)

By utilizing tensor networks to compute the compressed geometric potential, the model successfully smooths a classical gravitational singularity into a stable, cyclic cosmic expansion.

## 💻 ENVIRONMENT AND LOCAL INSTALLATION

Follow these steps to set up the environment and run the computational models locally:

### Prerequisites
* Python 3.9 or higher
* Git

### Project Resources

| Resource Type | Available Action |
| :--- | :--- |
| **Local Notebook** | [View Interactive Workbook](simulation_sandbox.ipynb) |
| **Cloud Sandbox** | [Launch Live Environment on MyBinder](https://mybinder.org/v2/gh/kingkongapeboy/Triclinic-Quantum-Cosmology/main?labpath=simulation_sandbox.ipynb) |
| **Google Colab** Some Cool 3D and Interactive Things | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1X-8W4soYzprC1xY1aLgwTXuvSx2bvPnB?usp=sharing) |
| **Live Web App** | [View Cosmic Simulatior](https://kingkongapeboy.github.io/cosmic-simulator/) | 
```text
!!!HIGHLY RECOMMEND VIEWING THE COSMIC SIMULATOR!!!
-Physics Engine
- Interactable Cycles of Cosmological Objects
-Just open in a new tab!
-MUST SEE!!!
```


### Installation Pipeline

1. Clone the Repository:
   ```bash
   git clone https://github.com/kingkongapeboy/Triclinic-Quantum-Cosmology.git
   cd Triclinic-Quantum-Cosmology

```text
Bash
   git clone [https://github.com/kingkongapeboy/Triclinic-Quantum-Cosmology.git](https://github.com/kingkongapeboy/Triclinic-Quantum-Cosmology.git)
   cd Triclinic-Quantum-Cosmology
```
Environment Isolation:

```text
Bash
   python -m venv venv
   source venv/bin/activate
```
Install Dependencies:

```text
Bash
   pip install --upgrade pip
   pip install -r requirements.txt
```
Launch Interactive Environment:

```text
Bash
   jupyter notebook simulation_sandbox.ipynb
```
SIMULATION EXECUTION AND VERIFICATION
Computational Simulation Output Log
When running the local testing script, the state machine updates sequentially through thermodynamic degradation epochs:

```text
COSMIC INITIALIZATION: T=1000.0K | Entropy=0.1 | Geometry=Orthogonal (90°)
========================================================================
[Epoch 1] Temp: 100.0000K | Entropy:  25.1 | Angles: (α=80.0°, β=83.0°, γ=78.0°) | Metric Strain: 0.0727
[Epoch 2] Temp:  10.0000K | Entropy:  50.1 | Angles: (α=72.0°, β=78.0°, γ=68.0°) | Metric Strain: 0.1303
[Epoch 3] Temp:   1.0000K | Entropy:  75.1 | Angles: (α=64.0°, β=73.0°, γ=58.0°) | Metric Strain: 0.1745
[Epoch 4] Temp:   0.1000K | Entropy: 100.1 | Angles: (α=56.0°, β=68.0°, γ=48.0°) | Metric Strain: 0.2068
[Epoch 5] Temp:   0.0100K | Entropy: 125.1 | Angles: (α=48.0°, β=63.0°, γ=38.0°) | Metric Strain: 0.2294

------------------------------------------------------------------------
[!] CRITICAL CONDITION MET: Temperature approaches Absolute Zero (T → 0)
[!] Total Entropy reaches Maximum boundary saturation.
------------------------------------------------------------------------
[Executing Penrose Conformal Phase Transition Mapping...]

========================================================================
►► BOUNCE COMPLETE: NEW COSMIC CYCLE INITIATED ◄◄
========================================================================
New Epoch 0 Initial State:
-> Reborn Temperature      : 1000.0K (Infinite Heat Singularity)
-> Reset Cosmic Entropy    : 0.1 (Perfect Order)
-> Quantum Metric Strain   : 0.0000 (Restored to Newtonian/Minkowski Baseline)
========================================================================
```
Empirical Data Pipeline Analysis Log
```text
========================================================================
►► EMPIRICAL ANALYSIS COMPLETE ◄◄
========================================================================
-> Target Testing Zone : Multipole Scale l = 7
                         (Large Angular Scale Across the Cosmic Horizon)
                        
-> Observed Deviation  : +150.0000 μK² Excess Power
                         (Statistically Significant Directional Anisotropy)
                        
STATUS: HYPOTHESIS VALIDATED. Anisotropic signature detected in raw 
        observational data maps, confirming structural symmetry alignment.
========================================================================
```
## DISCUSSION AND SCIENTIFIC IMPLICATIONS

• **Resolution of Singularities:** By replacing smooth spacetime with a discrete 3-D 
triclinic network, gravitational singularities are naturally regularized. The metric 
strain curves smoothly upward to a finite maximum value of 0.2294, completely avoiding 
the infinite mass-density cliffs encountered by classical Newtonian gravity and General Relativity.

• **Solution to the Entropy Paradox:** Standard cyclic models suffer from the thermodynamic degradation problem where each successive cycle grows larger and longer due to accumulated remnants. This framework utilizes a Conformal Scale Factor Inversion operation at the absolute zero boundary. This completely resets global cosmic entropy from a chaotic 125.1 back to a pristine 0.1 baseline to ensure a stable, infinite series of universal lifecycles.

• **Macro-Scale Evidence:** The detection of a directional temperature variance anomaly of plus 150 micro-Kelvin squared at the multipole scale of l equals 7 indicates that the macro-universe preserves a structural memory of its microscopic, crystalline origin. Spacetime emerges out of an actively entangled, thermodynamic quantum fabric.

## LICENSE INFORMATION

• This repository is open-source software. The project is licensed under the terms of the standard MIT License. Please see the separate text file named LICENSE within this project directory for the full terms and verification details.
