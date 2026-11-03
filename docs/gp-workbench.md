# Gaussian Process Workbench

**SimPilot — Machine Learning Module**

## 1. Overview

The Gaussian Process (GP) Workbench is the initial machine learning component of SimPilot.

It provides a research-oriented environment for predicting structural descriptors derived from simulation data, comparing regression models, and evaluating predictive uncertainty.

The workbench is designed to support reproducible scientific analysis and future integration with the SimPilot AI Agent.

## 2. Scientific Background

The initial application focuses on structural characteristics of Amphiphilic Polymer Conetworks (APCNs).

Simulation-derived concentration structure factors, S(q,t), are used to characterize spatial correlations and structural features.

Selected structural descriptors are extracted from these curves and used as prediction targets for Gaussian Process regression.

## 3. Prediction Targets

The current implementation supports three principal targets.

### 3.1 Characteristic Peak Wavevector (q*)

A characteristic wavevector extracted from an identifiable interior peak of the time-averaged structure factor.

Peak identification follows defined screening and consistency rules. A valid peak is not guaranteed for every dataset.

### 3.2 Normalized Spectral Excess (M)

A scalar structural descriptor calculated from the normalized structure factor over a specified wavevector band.

The calculation uses wavevector-bin weights based on the number of reciprocal-space directions.

### 3.3 Low-q Mean

A structural descriptor calculated from the low-wavevector region of the normalized structure factor.

The implementation uses equally weighted, complete reciprocal-space shells within a declared wavevector band.

These targets provide different structural summaries and should not be interpreted as direct measurements of complete three-dimensional morphology.

## 4. Dataset

The currently bundled research dataset includes:

- Five simulation-derived S(q,t) datasets.
- One simulation seed per recipe.
- Recipe labels: 1:21, 5:17, 8:14, 11:11, and 15:7.
- Available frames: 1490–1499.
- Data columns: time, q, and S.

The recipe labels are encoded as A/(A+B) for the current GP input.

The physical interpretation of these labels requires further confirmation. They should not automatically be described as measured polymer composition fractions.

The bundled dataset does not include complete particle trajectories, raw coordinates, or bond configurations.

## 5. Gaussian Process Models

The GP Workbench supports the following kernel options:

- Linear
- Radial Basis Function (RBF)
- Matérn 3/2
- Matérn 5/2
- Rational Quadratic

Two baseline approaches are also available:

- Mean baseline
- Linear regression baseline

The framework supports model comparison and predictive uncertainty analysis.

No individual kernel is assumed to be universally optimal.

## 6. Model Validation

The current validation framework uses a leave-one-recipe-out approach.

For each validation fold:

1. One recipe is excluded from model fitting.
2. Preprocessing is fitted using training data only.
3. Model hyperparameters are optimized without using the held-out recipe.
4. The excluded recipe is predicted.
5. Prediction accuracy and uncertainty are evaluated.

This procedure helps assess performance on previously unseen recipe conditions.

Evaluation methods include:

- Prediction error.
- Comparison against baseline models.
- Probabilistic scoring.
- Predictive uncertainty analysis.
- Per-recipe performance comparison.

Plots generated from models fitted to all available recipes are distinguished from held-out validation results.

## 7. Available Features

The GP Workbench currently includes:

- Local web-based research interface.
- Target selection and extraction.
- Multiple GP kernel options.
- Model training and validation.
- Predictive uncertainty reporting.
- Model comparison and visualization.
- Synthetic demonstration datasets.
- Saved-model prediction through command-line tools.
- Local report generation and experiment history.

The interface and command-line tools may support different feature sets.

## 8. Current Limitations

The initial research dataset contains five recipes with one seed each.

This limits the ability to establish:

- Independent seed variability.
- Robust uncertainty calibration.
- Generalization to substantially different simulation conditions.
- Reliability of long-term structural evolution predictions.
- Universal superiority of a particular GP kernel.

The current bundled dataset also does not independently establish an LJ-parameter-conditioned prediction model.

Additional simulation data and independent validation will be required before making broader performance claims.

## 9. Integration with SimPilot

The GP Workbench is intended to become a computational tool within the proposed SimPilot platform.

The planned workflow is:

**Research Question → Target Selection → GP Prediction → Uncertainty Analysis → Researcher Review**

Future AI Agent integration may enable:

- Automated dataset checking.
- Model and target selection.
- Prediction requests.
- Candidate simulation ranking.
- Research report generation.
- Human-approved simulation validation.

These integrated AI Agent capabilities remain under development.

## 10. Future Development

Planned improvements include:

- Expanded and independently validated simulation datasets.
- Additional structural prediction targets.
- Better characterization of model uncertainty.
- Comparison of candidate simulation-selection strategies.
- Hardware acceleration and performance benchmarking.
- Integration with the SimPilot AI Agent.
- Comparison and complementary analysis with future FNO models.

The GP Workbench serves as the initial implemented machine learning component of the broader SimPilot research platform.
