# SimPilot

### Where Machine Learning and AI Agents Unite for Scientific Discovery

**ASUS UGen AI League 2026 | Stage I Proposal**

**Team:** LLM說什麼都隊  
**Institution:** National Tsing Hua University

---

## 1. Project Overview

**SimPilot** is a proposed AI-assisted scientific research platform that integrates machine learning, local AI agents, and computational simulation workflows.

Our goal is to help researchers answer scientific questions more efficiently by combining the predictive capabilities of machine learning with the planning and tool-calling capabilities of AI agents.

The platform is designed around three principles:

- **Predict:** Use machine learning surrogate models to estimate scientific quantities and quantify prediction uncertainty.
- **Act:** Use AI agents to coordinate computational tools, analyze results, and recommend informative simulation tasks.
- **Verify:** Keep researchers in control through human approval, independent validation, and physics-based simulations.

The initial case study focuses on **Amphiphilic Polymer Conetworks (APCNs)**, using simulation-derived structural data to demonstrate the proposed workflow.

The machine learning framework includes:

- **Gaussian Process (GP):** Structural descriptor prediction and uncertainty estimation.
- **Fourier Neural Operator (FNO):** Planned spatial morphology and temporal evolution prediction.

SimPilot is intended to support future research applications through a modular prediction target architecture.

**Current Status:** Stage I Prototype — GP Workbench Available; AI Agent Integration and FNO Development Planned.

## 2. Motivation and Problem Statement

Scientific simulations are essential for understanding complex physical and material systems. However, computational research often requires repeated simulations, manual analysis, and substantial computing resources.

A conventional research workflow may include:

1. Preparing simulation configurations.
2. Submitting jobs to a high-performance computing (HPC) cluster.
3. Waiting for computational resources.
4. Executing numerical simulations.
5. Transferring and processing simulation outputs.
6. Analyzing and visualizing results.

This workflow introduces several challenges:

- Long simulation and queue times.
- High computational costs for repeated parameter exploration.
- Manual coordination between different scientific tools.
- Difficulty selecting the most informative simulation conditions.
- Limited integration between numerical simulation, machine learning, and research interpretation.

### Our Approach

Instead of performing a complete simulation for every new research question, SimPilot aims to use existing simulation data to provide initial predictions.

An AI agent can then help identify conditions that require further validation, while researchers retain approval authority over computationally expensive simulation runs.

The proposed workflow follows a **human-in-the-loop active learning** strategy:

**Predict → Recommend → Researcher Approval → Simulate → Validate → Update**

The objective is not to replace scientific simulations, but to reduce unnecessary repetitions and improve the efficiency of computational research.

## 3. Core Platform Features

### 3.1 Machine Learning Prediction

SimPilot incorporates machine learning surrogate models for predicting scientific quantities from simulation-derived datasets.

The existing GP Workbench supports structural descriptor prediction, model comparison, and predictive uncertainty analysis.

Future model extensions may include:

- Random Forest
- XGBoost
- Neural Networks
- Fourier Neural Operators
- Other compatible scientific machine learning architectures

Additional models will require suitable data interfaces and independent validation before integration.

### 3.2 Local AI Agent — In Development

The proposed AI agent will serve as an interface between researchers and computational tools.

Planned capabilities include:

- Understanding research questions expressed in natural language.
- Checking available datasets and model configurations.
- Selecting suitable prediction and analysis tools.
- Submitting authorized machine learning tasks.
- Monitoring computational workflows.
- Interpreting model outputs and predictive uncertainty.
- Recommending candidate simulation conditions.
- Generating research reports.

Scientific numerical results should originate from validated computational tools rather than unsupported language-model generation.

### 3.3 Human-in-the-Loop Workflow

SimPilot is designed to preserve researcher control over important computational decisions.

The proposed workflow includes:

- Researcher-selected models and parameters.
- Visible job progress and execution logs.
- Approval checkpoints before selected computational actions.
- Explicit researcher authorization before launching HPC simulation jobs.
- Traceable model predictions and validation reports.

The full AI agent monitoring and approval workflow remains a planned integration component.

## 4. Machine Learning Framework

### 4.1 Gaussian Process Workbench

The **Gaussian Process (GP) Workbench** is the initial machine learning component of SimPilot.

It uses simulation-derived structural data to build regression models and compare their predictive performance.

The available research implementation supports three principal targets:

**Characteristic Peak Wavevector — q\***

A characteristic wavevector extracted from an identifiable peak in the time-averaged structure factor under defined screening rules.

**Normalized Spectral Excess — M**

A scalar descriptor calculated from the normalized structure factor over a specified wavevector band.

**Low-q Mean**

A structural descriptor derived from the low-wavevector region using defined shell-averaging procedures.

These quantities help characterize structural correlations in the simulated system. They do not independently establish complete three-dimensional morphology or phase connectivity.

#### GP Model Features

The GP Workbench includes:

- Linear, RBF, Matérn 3/2, Matérn 5/2, and Rational Quadratic kernel options.
- Mean and linear regression baselines.
- Leave-one-recipe-out validation.
- Training-fold-only preprocessing.
- Predictive uncertainty estimates.
- Model comparison and evaluation reports.
- A local web-based research interface.

The bundled example dataset contains five real simulation-derived structure-factor datasets, with one seed per recipe.

These data support preliminary model development and evaluation, but do not establish reliable seed variability or universal model performance.

Additional research targets may include scattering peak positions, characteristic structural lengths, and time-dependent scattering quantities.

The definitions and availability of these targets must be confirmed for each dataset.

### 4.2 Fourier Neural Operator — Planned

The **Fourier Neural Operator (FNO)** is proposed as an additional machine learning component for predicting spatial morphology fields.

Unlike scalar regression models, neural operators can learn mappings between spatially distributed input and output fields.

The proposed FNO research direction focuses on predicting the evolution of phase-separated structures.

Potential inputs include:

- Initial spatial concentration or composition fields.
- Selected simulation parameters.
- Prediction time intervals.
- Relevant physical descriptors.

The proposed output is a predicted spatial field:

**φ(r, t + Δt)**

where φ represents a spatial concentration or composition field.

Candidate model architectures include:

- Fourier Neural Operator (FNO)
- U-FNO
- Multi-Head Neural Operator (MHNO)

Potential tasks include:

- Predicting future spatial morphologies.
- Learning temporal evolution of concentration fields.
- Comparing predicted and reference phase structures.
- Evaluating structural characteristics derived from predicted fields.

The proposed FNO workflow requires spatially resolved simulation data. The availability and mapping of FPD-style concentration fields and C++ simulation outputs must be established before training.

**Development Status:** Planned research and validation; full APCN-specific FNO performance has not yet been established.

### 4.3 Modular Prediction Target Architecture

Different scientific questions may require different prediction targets.

SimPilot proposes a **Target Module** that converts simulation outputs into representations suitable for specific machine learning tasks.

The architecture separates target-specific scientific processing from reusable model training and validation components.

Two primary target categories are proposed:

| Target Category | Model Approach | Example Outputs |
|---|---|---|
| Scalar Targets | Gaussian Process | q*, M, low-q mean, characteristic structural descriptors |
| Field Targets | Fourier Neural Operator | Spatial concentration fields and morphology evolution |

This modular approach is intended to support additional scientific questions without redesigning the complete research workflow.

Different targets may still require independent models, preprocessing procedures, and validation metrics.

## 5. Proposed System Architecture

SimPilot proposes a local AI and machine learning platform using two ASUS UGen computing nodes.

<img width="3200" height="1960" alt="SimPilot system architecture" src="https://github.com/user-attachments/assets/43291c7a-0ff4-41a6-9e73-f4768a664c91" />

*Figure 1. Proposed SimPilot architecture integrating a local AI agent, a machine learning engine, a data layer, and researcher-approved HPC simulations. The GP Workbench is the initial available component; additional model and agent capabilities are under development or planned.*

### 5.1 ASUS UGen Node 1 — AI Agent

**Proposed Hardware:** Intel Arc Pro B70, 32 GB

Planned responsibilities:

- Local LLM inference.
- Natural-language research interaction.
- Tool calling and workflow coordination.
- Job monitoring and human approval checkpoints.
- Prediction interpretation and reporting.
- Candidate simulation recommendations.

A locally deployed LLM is intended to reduce dependence on external AI APIs.

Candidate inference technologies include Ollama and Intel-compatible local inference frameworks, subject to compatibility and performance testing.

### 5.2 ASUS UGen Node 2 — Machine Learning Engine

**Proposed Hardware:** Intel Arc Pro B70, 32 GB

Planned responsibilities:

- GP model training and prediction.
- Kernel and hyperparameter comparison.
- Cross-validation and uncertainty evaluation.
- Future FNO training and inference.
- Model performance reporting.

Potential technologies include PyTorch XPU and GPyTorch.

Deployment feasibility, GPU memory consumption, and training performance will be measured during Stage II.

### 5.3 HPC Simulation Environment

The APCN research workflow uses **C++-based molecular dynamics simulations** supported by HPC resources.

The Stage I proposal identifies HKUST (Guangzhou) and Slurm-based job execution as the computational workflow for the case study.

Simulation outputs provide reference data for structural analysis, machine learning development, and independent validation.

HPC simulation execution will remain subject to researcher authorization.

### 5.4 Data Management

The proposed data layer will manage:

- Versioned scientific datasets.
- Simulation-derived structural measurements.
- Trained machine learning models.
- Prediction outputs and evaluation reports.
- Computational logs and experiment records.

The architecture prioritizes local model inference and controlled research data access.

Any transfer between local computing resources, institutional HPC systems, or optional backup services must follow applicable data-access and research collaboration requirements.

## 6. Case Study: Amphiphilic Polymer Conetworks

### 6.1 Material Background

Amphiphilic Polymer Conetworks (APCNs) contain covalently connected hydrophilic and hydrophobic polymer components.

Their nanoscale phase-separated structures can influence swelling behavior, mechanical response, optical properties, and transport characteristics.

Computational simulations provide insights into the relationship between structural organization and phase-separation behavior.

### 6.2 Existing Simulation Workflow

The APCN case study follows a computational research workflow involving:

**C++ Model Preparation → HPC Job Submission → Molecular Dynamics Simulation → Data Transfer → Python-Based Structural Analysis**

Scattering-related structural analysis may include:

- Structure factors, S(q,t).
- Scattering intensity profiles, I(q), where appropriately defined.
- Characteristic peak wavevectors.
- Domain spacing estimates.
- Structural evolution over time.

These quantities are related but should not be treated as interchangeable without their corresponding normalization and physical definitions.

### 6.3 Case Study Scope

The current research focuses on a specific APCN system.

Simulation studies can investigate selected interaction conditions, including Lennard-Jones interaction parameters, while maintaining prescribed material and temperature conditions.

The bundled GP Workbench dataset currently uses five recipe-ratio labels. Their physical interpretation must be confirmed before identifying the model input directly with a particular polymer fraction or Lennard-Jones parameter.

The APCN case study demonstrates how simulation-derived data can support surrogate modeling and subsequent scientific decisions.

### 6.4 Example Research Scenario

A researcher asks:

*“What characteristic domain spacing should I expect under a proposed simulation condition, and is an additional MD run necessary?”*

The proposed SimPilot workflow is:

1. The AI agent interprets the research question.
2. Available simulation datasets and prediction models are checked.
3. A suitable Target Module prepares the requested prediction.
4. The GP model provides a predicted value and uncertainty estimate.
5. Candidate simulation conditions are ranked according to a validated selection strategy.
6. The researcher reviews and approves any proposed MD run.
7. New simulation results are used for validation and potential model updating.

This scenario describes the intended integrated workflow. It should not be interpreted as proof that the full autonomous coordination and active-learning loop has already been implemented.

## 7. Model Validation and Evaluation

Scientific validation is a central component of the proposed platform.

### 7.1 GP Validation

The initial GP workflow includes:

- Leave-one-recipe-out validation.
- Separation of training and held-out observations.
- Training-only feature preprocessing.
- Comparison against mean and linear baselines.
- Error and probabilistic scoring.
- Reporting of predictive uncertainty.

Model comparisons must distinguish predictions on held-out recipes from curves fitted using all available observations.

### 7.2 FNO Validation — Planned

Potential validation procedures include:

- Independent simulation-case holdout.
- Relative spatial field error.
- Temporal rollout error.
- Characteristic domain-size agreement.
- Structure-factor consistency.
- Comparison with reference morphology evolution.

Spatial and temporal normalization parameters should be fitted using training data only.

### 7.3 Stage II Performance Targets

The Stage I proposal identifies the following future evaluation targets:

| Metric | Proposed Target |
|---|---|
| Prediction error | Below 10% against an appropriately defined held-out MD reference |
| Simulation run saving | 20% reduction at comparable prediction accuracy |
| Agent response time | Approximately 30 seconds for the specified interaction task |

Simulation run saving is defined as:

**Run Saving = 1 − N_agent / N_baseline**

where N represents the number of MD simulations required to reach a comparable prediction error.

These values are **Stage II targets, not verified performance results**.

The evaluation protocol, baseline definition, uncertainty calibration, and computational cost measurements will be documented alongside future benchmarks.

## 8. Repository Structure

The repository is organized to separate scientific documentation, machine learning components, and future agent integration.

Principal components include:

- **docs/** — Proposal documents, meeting notes, scientific references, and system design.
- **GP Workbench** — Existing structural-target extraction, GP training, prediction, and validation tools.
- **notebooks/** — Exploratory research and machine learning experiments.
- **src/** — Shared computational tools and application integration.
- **tests/** — Program and model validation.
- **README.md** — Main project introduction.

Planned additions include:

- **FNO module** — Spatial field preparation, neural operator architectures, training, and evaluation.
- **AI Agent module** — Local LLM inference, tool interfaces, orchestration, and researcher approval workflows.
- **Benchmark documentation** — Reproducible performance tests and simulation-run comparisons.

The exact package paths and installation instructions are maintained with the corresponding code components.

Research data and source code must be shared in accordance with their applicable ownership, attribution, and licensing requirements.

## 9. Development Roadmap

### Stage I — Initial Prototype

- [x] Establish the project repository.
- [x] Prepare initial simulation-derived datasets.
- [x] Develop the GP Workbench.
- [x] Implement selected structural-target extraction methods.
- [x] Implement initial GP model comparison and evaluation tools.
- [x] Define the proposed system architecture.
- [ ] Complete an independently validated end-to-end agent workflow.
- [ ] Complete APCN-specific FNO development and validation.

### Stage II — Deployment and Evaluation Plan

**November 2026 — Deployment**

- [ ] Prepare ASUS UGen development hardware.
- [ ] Deploy and test a compatible local LLM.
- [ ] Evaluate GP execution on Intel GPU hardware.
- [ ] Develop and test the initial FNO pipeline.
- [ ] Integrate AI agent tool interfaces.

**Late November to Early December 2026 — Measurement**

- [ ] Evaluate held-out prediction accuracy.
- [ ] Compare simulation recommendations against a defined baseline.
- [ ] Measure model training and inference performance.
- [ ] Record GPU memory consumption.
- [ ] Measure end-to-end agent response time.
- [ ] Validate researcher approval and logging workflows.

**December 2026 — Delivery**

- [ ] Prepare a reproducible demonstration.
- [ ] Finalize technical documentation.
- [ ] Publish approved benchmark results.
- [ ] Prepare the demonstration video and final presentation.

The proposed milestones are subject to competition progress, resource availability, and scientific validation results.

## 10. Expected Impact

SimPilot aims to provide a reusable foundation for AI-assisted computational research.

Potential benefits include:

1. **Reduced Simulation Overhead:** Avoid selected repetitive computations through validated surrogate predictions.
2. **More Informative Simulation Selection:** Prioritize new simulations based on model uncertainty and research objectives.
3. **Researcher-Controlled Automation:** Integrate intelligent tool orchestration with explicit scientific oversight.
4. **Flexible Prediction Targets:** Support scalar and spatial-field models within a modular architecture.
5. **Local Computing and Data Control:** Enable on-premise AI inference and controlled research data management.
6. **Scientific Reproducibility:** Preserve clear records of datasets, model configurations, validation results, and computational decisions.

The longer-term vision is to extend SimPilot beyond the initial APCN case study to other simulation-intensive research applications.

## 11. References

Relevant scientific publications and technical resources are collected in:

**[View References](docs/references.md)**

Topics include:

- Amphiphilic Polymer Conetworks.
- Viscoelastic phase separation.
- Gaussian Process modeling.
- Polymer machine learning.
- Fourier Neural Operators, U-FNO, and MHNO.
- Scientific machine learning and structural validation.
- AI agents and computational workflow automation.

## 12. Development Status and Limitations

SimPilot is under active research and development.

**Available Components**

- Initial GP Workbench.
- Selected structure-factor-derived prediction targets.
- Kernel and baseline model comparisons.
- Local GP research interface.
- Initial simulation-derived example datasets and evaluation procedures.

**In Development / Planned**

- Full local LLM and AI Agent integration.
- Automated candidate simulation ranking.
- Human-in-the-loop HPC orchestration.
- FNO-based spatial morphology prediction.
- Integrated GPU deployment on ASUS UGen hardware.
- End-to-end acceleration benchmarks.

Current results should be interpreted within the limitations of the available datasets and evaluation protocols.

The platform does not claim to replace molecular dynamics simulations, guarantee accurate extrapolation, or provide experimentally validated material properties without further scientific verification.

---

**SimPilot — Predict. Act. Verify.**
