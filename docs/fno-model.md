# Fourier Neural Operator (FNO) — Morphology Prediction

**SimPilot | Scientific Machine Learning Module**

**Development Status: Research and Validation in Progress / Planned Integration**

## 1. Overview

The Fourier Neural Operator (FNO) is a proposed machine learning component of SimPilot for predicting spatial morphology evolution in phase-separating systems.

While the existing Gaussian Process (GP) Workbench focuses on selected structural descriptors, the FNO module aims to predict spatially resolved fields describing material morphology.

The initial research application focuses on Amphiphilic Polymer Conetworks (APCNs) and related phase-separation simulations.

## 2. Research Motivation

Numerical simulations can provide detailed information about the spatial and temporal evolution of phase-separated structures.

However, generating long simulation trajectories and analyzing three-dimensional morphology fields may require substantial computational resources.

FNO offers a potential data-driven approach for approximating mappings between spatial fields.

The proposed objectives are to:

- Predict spatial morphology evolution from available simulation states.
- Learn relationships between initial configurations, simulation parameters, and future spatial structures.
- Explore alternatives to repeated full simulations within validated conditions.
- Integrate field predictions with structural analysis and visualization.

The feasibility and computational benefits of this approach require independent evaluation.

## 3. Model Architecture

The Fourier Neural Operator learns mappings between functions using transformations in Fourier space.

Candidate neural operator architectures include:

### 3.1 Fourier Neural Operator (FNO)

FNO uses Fourier-domain transformations to learn spatial relationships in field-based simulation data.

It serves as the initial reference architecture for full-field prediction experiments.

### 3.2 U-FNO

U-FNO extends the Fourier Neural Operator architecture by incorporating U-Net-inspired components.

It will be considered as a candidate for representing local and global spatial features.

### 3.3 Multi-Head Neural Operator (MHNO)

MHNO is an additional candidate architecture for modeling temporal and spatial evolution.

Its applicability to APCN morphology prediction will be evaluated against relevant reference simulations.

These architectures are research candidates. Their relative performance has not yet been established for the target APCN dataset.

## 4. Proposed Input and Output

### 4.1 Model Inputs

Potential model inputs include:

- Initial spatial concentration or composition fields.
- Spatial distributions of different material components.
- Selected simulation parameters.
- Prediction time intervals.
- Relevant physical descriptors, where available.

The Stage I proposal identifies FPD concentration fields, including φA and φB, as candidate field representations.

The relationship between these proposed fields and the available C++ molecular dynamics simulation outputs must be established during data preparation.

### 4.2 Prediction Outputs

The proposed FNO module aims to predict spatial field evolution.

A possible prediction mapping is:

**[φA(r,t), φB(r,t), simulation parameters, Δt] → [φA(r,t+Δt), φB(r,t+Δt)]**

Here, φA and φB represent spatial concentration or composition fields.

This mapping illustrates a candidate model design rather than a confirmed implementation.

The predicted fields may subsequently be used to analyze:

- Phase-separated morphology.
- Spatial concentration distributions.
- Characteristic structural length scales.
- Structure-factor-related quantities.
- Temporal evolution of phase-separated structures.

## 5. Proposed Data Preparation

The FNO module requires spatially resolved datasets suitable for field-based learning.

The proposed data preparation workflow includes:

1. Obtain spatially resolved reference simulation data.
2. Define the physical field quantities and spatial coordinates.
3. Construct consistent spatial grids.
4. Establish input and prediction time windows.
5. Apply normalization using training data only.
6. Generate training, validation, and testing datasets.
7. Document simulation parameters and data provenance.

The current GP Workbench's bundled structure-factor CSV files do not provide sufficient information to reconstruct unique three-dimensional concentration fields.

Additional simulation outputs are therefore required for full-field FNO training.

## 6. Proposed Training and Validation

The Stage I proposal describes a validation workflow based on holding out entire simulation recipes.

### 6.1 Validation Strategy

- Separate complete simulation runs or recipes between training and evaluation.
- Use leave-one-ratio-out evaluation where appropriate for the available dataset.
- Fit normalization parameters using training data only.
- Evaluate predictions on held-out simulation cases.
- Compare predictions against independent reference fields.

Temporal frames from the same trajectory must not be treated as independent simulation runs when constructing training and testing splits.

### 6.2 Evaluation Metrics

Potential evaluation criteria include:

**Spatial Prediction Accuracy**

- Relative L2 field error.
- Spatial reconstruction error.
- Comparison with reference morphology fields.

**Temporal Prediction Accuracy**

- Error during multi-step rollout.
- Stability of predicted morphology evolution.
- Agreement with reference temporal trends.

**Structural Consistency**

- Structure-factor characteristics.
- Characteristic peak wavevectors.
- Domain size evolution.
- Spatial morphology consistency.

Evaluation metrics will be finalized after the target fields, simulation geometry, and prediction tasks are defined.

## 7. Integration with SimPilot

The planned FNO module will complement the existing GP Workbench.

| Component | Main Research Function |
|---|---|
| GP Workbench | Structural descriptor prediction and uncertainty analysis |
| FNO Module | Spatial field prediction and morphology evolution |
| Target Module | Target-specific data representation and preparation |
| AI Agent | Research workflow coordination and tool integration |

The proposed workflow is:

**Research Question → Target Module → FNO Prediction → Structural Analysis → Researcher Review**

FNO predictions may be integrated into the broader SimPilot analysis and reporting framework after independent validation.

## 8. Computing Environment

The Stage I proposal plans to evaluate deployment using ASUS UGen hardware with Intel Arc Pro B70 GPUs.

Candidate technologies include:

- Python
- PyTorch
- Intel GPU / XPU acceleration
- Fourier Neural Operator implementations

GPU memory requirements and training performance depend on:

- Spatial grid resolution.
- Number of input and output channels.
- Model architecture and Fourier modes.
- Batch size.
- Temporal rollout length.

Hardware compatibility and performance will be established through deployment testing.

## 9. Current Status and Limitations

The FNO module is part of the SimPilot research and development roadmap.

The Stage I presentation includes a visual comparison labeled as an APCN three-dimensional morphology result.

Before presenting this as a verified project result, its dataset provenance, model configuration, and quantitative validation must be documented.

Outstanding tasks include:

- Confirming the source and availability of spatial field data.
- Defining input and output representations.
- Establishing reproducible training configurations.
- Evaluating candidate neural operator architectures.
- Validating spatial and temporal predictions.
- Measuring inference speed and computational requirements.
- Integrating validated models with SimPilot.

No generalization, simulation speedup, or full-field prediction accuracy is claimed without corresponding experimental evidence.

## 10. References

**[1] Li et al. (2021)**

"Fourier Neural Operator for Parametric Partial Differential Equations."

International Conference on Learning Representations (ICLR).

https://arxiv.org/abs/2010.08895

**[2] Wen et al. (2022)**

"U-FNO—An Enhanced Fourier Neural Operator-Based Deep-Learning Model for Multiphase Flow."

Advances in Water Resources, 163, 104180.

https://doi.org/10.1016/j.advwatres.2022.104180

**[3] Eshaghi et al. (2025)**

"Multi-Head Neural Operator for Modelling Interfacial Dynamics."

arXiv:2507.17763.

https://arxiv.org/abs/2507.17763

For the complete scientific bibliography, see [Project References](references.md).
