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

### 4.1 Model
