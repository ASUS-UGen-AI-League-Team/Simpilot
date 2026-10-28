# LLM說什麼都隊

**ASUS UGen AI League 2026 | Stage I Proposal**

## Project Title

AI-Assisted Prediction and Analysis of Phase-Separated Morphology in Amphiphilic Polymer Conetworks

## 1. Project Overview

This project proposes an AI-assisted computational framework for predicting and analyzing the phase-separated morphology of **Amphiphilic Polymer Conetworks (APCNs)**.

By integrating **C++-based numerical simulations**, **machine learning surrogate models**, and **AI Agents**, we aim to accelerate structural prediction, reduce repetitive computational workloads, and streamline scientific simulation and analysis workflows.

The proposed machine learning framework consists of two complementary approaches:

- **Gaussian Process (GP):** Prediction of scattering-related structural descriptors, including characteristic wavevectors and other quantities derived from simulation data.
- **Fourier Neural Operator (FNO) — Planned:** Prediction of spatial phase-separated morphology and its temporal evolution using simulation-derived concentration fields.

An AI Agent-assisted workflow is proposed to coordinate model selection, prediction, data analysis, and visualization.

The long-term objective is to establish an extensible computational platform that supports both structural characterization and spatial morphology prediction.

**Current Status:** Stage I — Initial GP Implementation and Planned FNO Development

## 2. Background

Amphiphilic Polymer Conetworks (APCNs) are polymer networks composed of covalently interconnected hydrophilic and hydrophobic components.

Due to thermodynamic incompatibility between these components, APCNs can exhibit nanoscale phase-separated structures.

Their morphology can influence important material properties, including:

- Swelling behavior
- Mechanical properties
- Optical properties
- Transport characteristics

Understanding phase-separation mechanisms and structural evolution is essential for investigating the behavior of these polymer networks.

Our research focuses on a specific APCN system investigated through C++-based numerical simulations.

The temperature is held constant, while selected Lennard-Jones interaction parameters can be varied to examine their influence on structural behavior.

Scattering-related quantities, such as structure factors and characteristic wavevectors, provide information about structural length scales and phase-separation evolution.

Spatial concentration fields can provide additional information about the distribution and evolution of polymer-rich and polymer-poor regions.

However, exploring different simulation conditions and analyzing complex spatial structures may require substantial computational resources.

## 3. Problem Statement

The existing computational workflow relies on **C++-based numerical simulations** to investigate polymer phase separation and structural evolution.

The workflow generally involves:

1. Preparing simulation configurations and interaction parameters.
2. Executing C++ numerical simulations using available computing resources.
3. Generating and collecting simulation outputs.
4. Processing structural and trajectory data.
5. Calculating scattering-related quantities and analyzing structural evolution.
6. Visualizing and interpreting simulation results.

Several challenges may arise:

- High computational costs associated with repeated simulations.
- Time-consuming exploration of different interaction parameters.
- Dependence on available high-performance computing (HPC) resources.
- Manual processing and analysis of simulation outputs.
- Difficulty predicting complex spatial morphology evolution.
- Limited integration between simulation, machine learning, and visualization tools.

These challenges motivate the development of an AI-assisted computational framework that can reuse existing simulation data for structural prediction and support more efficient scientific workflows.

## 4. Proposed Solution

We propose a modular computational framework combining four components:

1. Gaussian Process-based structural prediction.
2. Fourier Neural Operator-based morphology prediction (planned).
3. A modular prediction target system.
4. AI Agent-assisted workflow coordination.

### 4.1 Gaussian Process-Based Surrogate Model

A **Gaussian Process (GP)-based surrogate modeling framework** has been developed for investigating structural quantities derived from numerical simulations.

The GP Workbench includes functionality for extracting and analyzing selected structure-factor-related targets.

Current implemented targets include:

- **Characteristic Peak Wavevector, q\*:** A characteristic wavevector determined from an identifiable peak in the time-averaged structure factor under defined screening rules.
- **Normalized Spectral Excess, M:** A structure-factor-derived scalar quantity calculated over a specified wavevector range.
- **Low-q Mean:** A low-wavevector structural descriptor calculated using defined shell-averaging procedures.

Additional scattering-related research targets may include:

- Scattering intensity or structure-factor profiles, I(q) or S(q), according to the adopted definition.
- Peak position, q_peak.
- Time evolution of characteristic peak positions, q_peak(t).

Where applicable, a characteristic structural length scale can be estimated using:

L(t) ≈ 2π / q_peak(t)

The existing GP Workbench provides model comparison, baseline models, cross-validation, and predictive uncertainty analysis.

The currently bundled GP dataset uses five recipe labels. The physical interpretation of these labels and their relationship to future Lennard-Jones parameter studies require confirmation.

The GP approach is intended to accelerate the prediction of selected structural descriptors within validated conditions rather than directly reconstruct complete three-dimensional morphologies.

### 4.2 Fourier Neural Operator (FNO) — Planned

In addition to GP-based structural prediction, we plan to investigate **Fourier Neural Operators (FNOs)** for predicting the spatial evolution of phase-separated morphologies in APCNs.

FNO is a neural operator architecture designed to learn mappings between functions, making it a potential approach for learning the evolution of spatial fields generated by numerical simulations.

Unlike the GP Workbench, which currently focuses on selected structural descriptors, the proposed FNO module will investigate **full-field morphology prediction**.

Potential model inputs include:

- Initial spatial concentration or composition fields.
- Selected Lennard-Jones interaction parameters.
- Simulation time or prediction time interval.
- Additional physical descriptors, where available and scientifically justified.

The proposed output is a predicted spatial morphology field, potentially represented as:

**φ(r, t + Δt)**

where φ describes a spatial concentration or composition field.

Potential research objectives include:

- Predicting future phase-separated structures from an initial state.
- Investigating spatial morphology evolution over time.
- Evaluating how interaction parameters influence structural evolution.
- Reducing the computational requirements of selected simulation tasks within validated conditions.

The initial development will focus on establishing suitable field representations, preparing simulation datasets, and conducting feasibility tests.

Two-dimensional proof-of-concept experiments may be considered before extending the model to full three-dimensional morphology prediction.

**Development Status:** The FNO module is currently planned and has not yet been implemented or validated.

### 4.3 Modular Prediction Target System

The proposed framework adopts a modular architecture to support different scientific prediction targets.

A **Target Module** converts simulation data into suitable target representations according to the research question.

For example:

- Scattering-derived structural descriptors can be prepared for GP-based regression.
- Spatial concentration fields can be prepared for FNO-based morphology prediction.
- Additional research targets may be introduced through corresponding data preparation and validation procedures.

The purpose of this modular design is to separate target-specific scientific processing from reusable machine learning infrastructure.

Different prediction tasks may require different model configurations, training procedures, and evaluation metrics.

By providing compatible data interfaces, the framework aims to support future research extensions without rebuilding the entire computational workflow.

### 4.4 AI Agent-Assisted Workflow

An **AI Agent-based system** is proposed to coordinate computational tasks and simplify interactions between researchers, numerical simulations, and machine learning models.

Potential functions include:

- Interpreting user-defined research requests.
- Identifying suitable prediction targets and computational tools.
- Preparing simulation and prediction inputs.
- Coordinating available C++ simulation tools.
- Executing validated GP models and future FNO models.
- Analyzing structural predictions and model uncertainty.
- Generating visualizations and research reports.
- Assisting researchers in identifying conditions requiring additional validation.

The AI Agent will primarily support workflow coordination and tool integration.

Numerical simulation execution and scientifically consequential decisions will remain subject to researcher approval.

## 5. Proposed System Architecture

The proposed **SimPilot** framework integrates numerical simulations, machine learning prediction modules, and AI-assisted workflow automation.

<img width="3200" height="1960" alt="042E26D7-DAA4-4F6F-848B-9BEE8D5CDF08" src="https://github.com/user-attachments/assets/43291c7a-0ff4-41a6-9e73-f4768a664c91" />

*Figure 1. SimPilot system architecture showing the proposed integration of a local AI Agent, GP Workbench, data management, and HPC-based numerical simulations. FNO is included as a planned extension.*

### 5.1 Simulation and Data Preparation

**C++ Numerical Simulation → Simulation Outputs → Data Preprocessing → Research Dataset**

C++-based numerical simulations provide reference data for investigating structural evolution and developing machine learning models.

Different prediction objectives require different representations of simulation data.

For GP-based structural prediction, simulation-derived structure factors and other structural quantities can be processed into scalar prediction targets.

For the planned FNO module, spatially resolved simulation data will be needed to construct suitable two-dimensional or three-dimensional concentration fields.

The availability, temporal resolution, and completeness of the required spatial data will be evaluated before FNO training.

### 5.2 Machine Learning Prediction

The proposed machine learning framework contains two complementary prediction pathways.

**Pathway A — Gaussian Process**

Simulation Data → Structural Target Extraction → GP Model → Structural Predictions

The GP Workbench focuses on selected structure-factor-related quantities and their predictive uncertainty.

**Pathway B — Fourier Neural Operator (Planned)**

Simulation Data → Spatial Field Construction → FNO Model → Predicted Spatial Morphology

The FNO module will investigate mappings between spatial states to predict morphology evolution.

Both pathways are intended to use a common framework for data management, experiment tracking, and scientific validation where appropriate.

However, the models will require task-specific preprocessing, training configurations, and evaluation methods.

### 5.3 AI Agent Integration

An AI Agent is planned to serve as the coordinating interface between researchers and computational tools.

The proposed workflow is:

**Researcher Request → AI Agent → Target Selection → GP / FNO / Simulation Tools → Analysis & Visualization**

The framework is intended to support two complementary research approaches:

**Simulation-Based Analysis**

Use C++ numerical simulations to investigate phase separation, characterize polymer structures, and generate reference data.

**Machine Learning-Based Prediction**

Use validated surrogate models to estimate selected structural characteristics or spatial fields without repeating a complete numerical simulation for every prediction request.

The detailed integration architecture will be refined as development progresses.

## 6. Model Evaluation

The proposed machine learning models will be evaluated against independent numerical simulation results.

Evaluation procedures will be selected according to the prediction target and model architecture.

### 6.1 GP Prediction Accuracy

Potential evaluation criteria include:

- Mean Absolute Error (MAE).
- Root Mean Squared Error (RMSE).
- Accuracy of characteristic wavevector predictions.
- Agreement between predicted and reference structural descriptors.
- Predictive uncertainty and probabilistic scoring.
- Comparison with mean and linear regression baselines.

Validation results will distinguish held-out predictions from models fitted to the complete available dataset.

### 6.2 FNO Morphology Prediction Accuracy — Planned

The FNO model will require evaluation of predicted spatial fields against corresponding reference simulation fields.

Potential evaluation criteria include:

- Spatial field prediction error.
- Relative L2 error.
- Agreement of spatial morphology patterns.
- Structure-factor consistency.
- Characteristic domain size and phase fraction.
- Stability of predictions over multiple time steps.

The choice of metrics will depend on the spatial field definition, temporal prediction task, and available simulation data.

### 6.3 Generalization and Physical Consistency

Model performance will be evaluated on appropriately separated simulation cases.

Where sufficient independent simulation data are available, validation may include previously unseen interaction conditions or initial configurations.

Different frames from the same simulation trajectory will not be treated as fully independent simulation runs.

For FNO-based predictions, relevant physical constraints and structural consistency checks may be considered during model development.

### 6.4 Computational Efficiency

Computational efficiency will be evaluated by comparing:

- GP and FNO inference time.
- Reference C++ simulation runtime.
- Data preparation and model training costs.
- Computational resources required for repeated prediction tasks.

Claims of computational acceleration will be supported by measured results rather than assumed from model architecture alone.

## 7. Repository Structure

The repository is organized into the following components:

- **docs/** — Project documentation, references, meeting notes, and system architecture.
- **gp-workbench/** — Existing GP-based structural prediction and evaluation tools.
- **notebooks/** — Jupyter notebooks for data exploration and machine learning experiments.
- **src/** — Source code for system integration, computational utilities, and AI Agent development.
- **tests/** — Testing and validation scripts.
- **requirements.txt** — Python package dependencies for applicable project components.
- **README.md** — Project overview and development information.

**Planned extension:**

- **fno-workbench/** — Future FNO data preprocessing, model implementation, training, and evaluation.

The existing numerical simulation software is written in C++. Its integration and distribution within this repository will depend on the final project architecture and applicable access permissions.

The FNO module may require a separate deep learning environment and hardware-specific dependencies.

## 8. Development Roadmap

### Phase 1 — Project Planning

- [x] Initialize the GitHub repository.
- [x] Establish the initial repository structure.
- [x] Identify the initial GP structural prediction targets.
- [ ] Finalize the integrated GP / FNO / AI Agent architecture.
- [ ] Complete the review of relevant scientific literature.

### Phase 2 — Gaussian Process Development

- [x] Prepare and preprocess initial simulation-derived data.
- [x] Develop and conduct preliminary evaluation of the GP-based surrogate model.
- [ ] Confirm the physical definitions and input variables for expanded prediction tasks.
- [ ] Validate model predictions against independent simulation results.
- [ ] Assess predictive uncertainty and generalization.
- [ ] Evaluate computational efficiency relative to C++ simulations.

### Phase 3 — Fourier Neural Operator Development

- [ ] Confirm the availability of spatial simulation data.
- [ ] Define the FNO input and output field representations.
- [ ] Prepare spatial field datasets from C++ simulation outputs.
- [ ] Develop an initial FNO proof of concept.
- [ ] Evaluate spatial morphology prediction accuracy.
- [ ] Investigate physics-informed constraints and temporal prediction stability.
- [ ] Assess computational performance and GPU requirements.

### Phase 4 — AI Agent Integration

- [ ] Design the AI Agent workflow and model interfaces.
- [ ] Integrate available GP prediction and analysis tools.
- [ ] Integrate the FNO model after independent validation.
- [ ] Implement automated visualization and reporting.
- [ ] Evaluate end-to-end system performance.

## 9. Expected Outcomes

The proposed framework aims to:

1. Demonstrate the feasibility of GP-based prediction of scattering-related structural characteristics in APCNs.
2. Investigate FNO-based prediction of spatial phase-separated morphology and its temporal evolution.
3. Develop a modular prediction framework supporting different scientific research targets.
4. Reduce the need for repetitive numerical simulations within validated parameter ranges.
5. Establish an integrated workflow connecting C++ simulations, machine learning, and structural analysis.
6. Develop an AI Agent-assisted interface for coordinating computational research tasks.
7. Support future development of AI-assisted polymer material analysis and design.

## 10. References

Relevant scientific publications and technical documentation are collected in:

**[View References](docs/references.md)**

The references cover:

- Amphiphilic Polymer Conetworks and nanoscale phase separation.
- Viscoelastic phase separation and structural evolution.
- Gaussian Process modeling.
- Machine learning in polymer research.
- Fourier Neural Operators and scientific machine learning.
- Scattering-based structural characterization.
- AI Agents and scientific workflow automation.

An important methodological reference for the proposed FNO module is:

**Li et al. (2021)** — "Fourier Neural Operator for Parametric Partial Differential Equations." *International Conference on Learning Representations (ICLR).*

Publication: https://mlanthology.org/iclr/2021/li2021iclr-fourier/

## 11. Project Status

This repository is currently under development for the **ASUS UGen AI League 2026 Stage I Proposal**.

The project builds upon C++ numerical simulations and an initial Gaussian Process Workbench for structural prediction and model evaluation.

The proposed Fourier Neural Operator module is a future research component intended to investigate full-field morphology prediction.

The AI Agent integration, unified workflow, additional validation, and computational acceleration assessment remain under development.

The current GP implementation and the proposed FNO module address different prediction targets and should not be interpreted as having equivalent levels of implementation or validation.

Detailed technical specifications, quantitative evaluations, and research results will be updated as the project progresses.
