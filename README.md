# LLM說什麼都隊

**ASUS UGen AI League 2026 | Stage I Proposal**

## Project Title

AI-Assisted Prediction and Analysis of Phase-Separated Morphology in Amphiphilic Polymer Conetworks

## 1. Project Overview

This project proposes an AI-assisted computational framework for predicting and analyzing the phase-separated morphology of **Amphiphilic Polymer Conetworks (APCNs)**.

By integrating **C++-based numerical simulations**, **Gaussian Process (GP) machine learning**, and **AI Agents**, we aim to accelerate structural analysis, reduce repetitive computational workloads, and streamline the simulation and analysis process.

The framework uses simulation-generated data to develop a machine learning surrogate model for predicting scattering-related structural characteristics, including scattering intensity profiles, characteristic peak positions, and their temporal evolution.

These predictions provide insights into the phase-separated structure and evolution of APCNs without necessarily reconstructing the complete three-dimensional polymer morphology.

**Current Status:** Stage I — Proposal Development and Initial Machine Learning Implementation

## 2. Background

Amphiphilic Polymer Conetworks (APCNs) are polymer networks composed of covalently interconnected hydrophilic and hydrophobic components.

Due to thermodynamic incompatibility between these components, APCNs can exhibit nanoscale phase-separated structures.

Their morphology can influence important material properties, including:

- Swelling behavior
- Mechanical properties
- Optical properties
- Transport characteristics

Understanding the relationships between polymer composition, network structure, and phase-separated morphology is essential for the design and optimization of functional polymer materials.

Numerical simulations provide valuable insights into phase separation mechanisms and structural evolution. However, investigating a wide range of material parameters and simulation conditions may require substantial computational resources.

Scattering-related structural quantities, such as intensity profiles and characteristic wavevectors, can be used to characterize the length scales and temporal evolution of phase-separated structures.

## 3. Problem Statement

The existing computational workflow relies on **C++-based numerical simulations** to investigate polymer phase separation and structural evolution.

The workflow generally involves:

1. Preparing simulation configurations and physical parameters.
2. Executing C++ numerical simulations, potentially using high-performance computing (HPC) resources.
3. Generating and collecting simulation outputs.
4. Processing simulation data for structural characterization.
5. Calculating scattering-related quantities and analyzing structural evolution.
6. Visualizing and interpreting simulation results.

Several challenges may arise:

- High computational costs associated with repeated simulations.
- Time-consuming exploration of different material parameters.
- Dependence on available computational resources.
- Manual processing and analysis of simulation outputs.
- Limited integration between simulation, prediction, and visualization tools.

These challenges motivate the development of a more efficient, AI-assisted computational framework capable of predicting selected structural characteristics using previously generated simulation data.

## 4. Proposed Solution

We propose a computational framework combining two major components:

1. A Gaussian Process-based surrogate model for structural prediction.
2. An AI Agent-assisted system for workflow coordination and automation.

### 4.1 Gaussian Process-Based Surrogate Model

A **Gaussian Process (GP)-based surrogate model** is being developed to predict structural characteristics associated with phase separation in APCNs.

The model uses data generated from C++ numerical simulations to learn relationships between simulation conditions and structural outputs.

Potential model inputs include:

- Polymer composition
- Crosslink density
- Particle interaction parameters
- Simulation conditions
- Simulation time
- Scattering wavevector, where applicable

The current prediction targets include:

**Scattering Intensity, I(q)**

Scattering intensity profiles provide information about the spatial organization and characteristic length scales of phase-separated polymer structures.

**Peak Position, q_peak**

The characteristic wavevector corresponding to the principal peak of the scattering intensity profile.

The associated characteristic structural length scale may be estimated as:

L = 2π / q_peak

where this relationship is appropriate for the analyzed structure.

**Time Evolution of Peak Position, q_peak(t)**

The temporal evolution of the characteristic wavevector provides information about phase-separation kinetics and structural coarsening.

By analyzing the relationship between characteristic wavevectors and simulation time, the evolution of structural length scales can be investigated.

These prediction targets are closely related, but they do not necessarily represent independent model outputs. For example, peak positions may be extracted from predicted scattering profiles rather than predicted by a separate model.

The detailed model inputs, output representations, and prediction procedures will be documented as development progresses.

In addition to numerical predictions, GP-based methods can provide predictive uncertainty estimates, which may help identify conditions requiring additional simulations or validation.

### 4.2 AI Agent-Assisted Workflow

An **AI Agent-based system** is proposed to coordinate computational tasks and simplify interactions between users, simulation tools, and machine learning models.

Potential functions include:

- Interpreting user-defined research requests.
- Preparing simulation and prediction inputs.
- Coordinating available C++ simulation tools.
- Executing trained GP prediction models.
- Processing and analyzing scattering-related structural data.
- Generating visualizations of scattering intensity profiles and temporal evolution.
- Organizing computational results and analysis reports.

The AI Agent will primarily support workflow automation and tool integration rather than replace the underlying numerical simulations or scientific validation.

## 5. Proposed System Architecture

The proposed framework integrates numerical simulations, machine learning predictions, and AI-assisted workflow automation.
<img width="3200" height="1960" alt="042E26D7-DAA4-4F6F-848B-9BEE8D5CDF08" src="https://github.com/user-attachments/assets/43291c7a-0ff4-41a6-9e73-f4768a664c91" />


### 5.1 Simulation and Data Preparation

**C++ Numerical Simulation → Simulation Outputs → Data Preprocessing → Reference Dataset**

C++-based numerical simulations provide the reference data required for machine learning development and structural characterization.

Relevant structural quantities are extracted from simulation results and prepared for training and evaluating GP models.

### 5.2 Machine Learning Prediction

**Simulation-Derived Dataset → GP Surrogate Model → Structural Prediction → Analysis & Visualization**

The GP model is designed to predict selected scattering-related structural quantities, potentially including:

- Scattering intensity profiles, I(q)
- Characteristic peak positions, q_peak
- Time-dependent characteristic wavevectors, q_peak(t)

The exact prediction procedure will depend on the final model implementation.

### 5.3 AI Agent Integration

An AI Agent will serve as a coordinating interface between users and computational tools.

The proposed integrated workflow is:

**User Request → AI Agent → Simulation / GP Prediction / Analysis Tools → Visualization & Results**

The framework is intended to support two complementary approaches:

**Simulation-Based Analysis**

Use C++ numerical simulations to investigate phase separation, characterize polymer structures, and generate reference data.

**Machine Learning-Based Prediction**

Use trained GP surrogate models to estimate selected structural characteristics without repeating the complete numerical simulation for every prediction request.

The detailed system architecture will be refined as the project progresses.

## 6. Model Evaluation

The GP-based surrogate model will be evaluated by comparing its predictions with independent reference simulation results.

### 6.1 Prediction Accuracy

Potential evaluation criteria include:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Agreement between predicted and reference scattering intensity profiles
- Accuracy of predicted or extracted peak positions

### 6.2 Structural Consistency

The predicted structural quantities will be examined through:

- Scattering intensity profiles, I(q)
- Characteristic peak positions, q_peak
- Time evolution of characteristic wavevectors, q_peak(t)
- Characteristic structural length scales
- Agreement with reference structural evolution trends

These evaluations will help determine whether the model captures relevant characteristics of the simulated phase-separated structures.

### 6.3 Predictive Uncertainty and Generalization

Where supported by the model implementation, GP predictive uncertainty will be evaluated.

Model performance on previously unseen simulation conditions will also be investigated to assess generalization.

Training and testing datasets will be separated appropriately to avoid data leakage, particularly when multiple observations originate from the same simulation trajectory.

### 6.4 Computational Efficiency

Computational efficiency will be evaluated by comparing:

- GP model inference time
- Reference C++ simulation runtime
- Computational resources required for repeated prediction tasks

Model training and data-generation costs will also be considered when assessing the overall computational benefit.

The final evaluation metrics will be selected according to the confirmed model outputs and available datasets.

## 7. Repository Structure

The repository is organized as follows:

- **docs/** — Project documentation, research references, and system design.
- **notebooks/** — Jupyter notebooks for data exploration, machine learning experiments, and analysis.
- **src/** — Project source code, simulation-related utilities, machine learning models, and AI integration components.
- **tests/** — Testing and validation scripts.
- **requirements.txt** — Python package dependencies for applicable project components.
- **README.md** — Project overview and development information.

The existing numerical simulation software is written in C++. Its integration and distribution within this repository will depend on the final project architecture and applicable access permissions.

## 8. Development Roadmap

### Phase 1 — Project Planning

- [x] Initialize the GitHub repository.
- [x] Establish the initial repository structure.
- [ ] Finalize the integrated system architecture.
- [x] Identify the initial structural prediction targets.
- [ ] Complete the review of relevant scientific literature.

### Phase 2 — Machine Learning Development

- [x] Prepare and preprocess initial simulation data.
- [x] Develop and conduct preliminary evaluation of a GP-based surrogate model.
- [ ] Document the final model input and output definitions.
- [ ] Validate model predictions against independent simulation results.
- [ ] Assess prediction uncertainty and generalization.
- [ ] Evaluate computational efficiency relative to C++ simulations.

### Phase 3 — AI Agent Integration

- [ ] Design the AI Agent workflow.
- [ ] Integrate simulation, prediction, and analysis tools.
- [ ] Implement automated visualization and reporting.
- [ ] Evaluate end-to-end system performance.

## 9. Expected Outcomes

The proposed framework aims to:

1. Demonstrate the feasibility of GP-based prediction of scattering-related structural characteristics in APCNs.
2. Characterize phase-separated structures through scattering intensity profiles, peak positions, and their temporal evolution.
3. Reduce the need for repetitive numerical simulations within validated parameter ranges.
4. Establish an integrated workflow connecting C++ simulations, machine learning, and structural analysis.
5. Develop an AI Agent-assisted interface for coordinating computational research tasks.
6. Support future applications of AI-assisted polymer material analysis and design.

## 10. References

Relevant scientific publications and technical documentation are collected in:

**[View References](docs/references.md)**

The references cover:

- Amphiphilic Polymer Conetworks and nanoscale phase separation
- Viscoelastic phase separation and structural evolution
- Gaussian Process modeling
- Machine learning in polymer research
- Scattering-based structural characterization

## 11. Project Status

This repository is currently under development for the **ASUS UGen AI League 2026 Stage I Proposal**.

The project builds upon C++ numerical simulations and initial Gaussian Process machine learning development.

The planned AI Agent integration, automated analysis workflow, and additional model validation remain under development.

The current prediction targets focus on scattering-related structural characteristics rather than direct reconstruction of complete three-dimensional polymer morphologies.

Detailed implementation procedures, quantitative model evaluations, and research results will be updated as the project progresses.
