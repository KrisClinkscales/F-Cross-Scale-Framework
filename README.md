# F-Cross-Scale-Framework
A universal statistical framework for cross-scale residual aggregation. Implements the F-cross-scale metric and beta-optimization for detecting density-dependent coupling in arbitrary astrophysical and cosmological datasets.
# Cross-Scale Residual Aggregation Analysis (F-hat)
**Author:** Kris Clinkscales  
**Date:** January 2026 | **DOI:** [10.5281/zenodo.18283205]

## Project Overview
This repository provides the Python implementation for the **Clinkscales Cross-Scale Metric**. This framework identifies systematic correlations in gravitational residuals across disparate scales, from kilometer-scale interferometry (LIGO) to Megaparsec-scale galactic surveys.

Unlike standard analyses that treat residuals as stochastic noise, this methodology tests if residuals show a coherent dependence on local mass-energy density (rho), providing a model-agnostic test for structured vacuum contributions or unmodeled physical effects.

---

## Mathematical Framework
The implementation follows the formalized statistical structure detailed in Section II of the 2026 manuscript.

### 1. Dimensionless Variables & Normalization
To ensure numerical stability across ~20 orders of magnitude, all quantities are rendered dimensionless. The raw aggregation (F) is transformed into a normalized statistic (F-hat):

> F-hat = F_cross-scale / Z

Where **Z** is the normalization factor (the square root of the sum of weights, variances, and density functions squared). Under the null hypothesis, **F-hat** converges to a standard normal distribution N(0,1), allowing for direct Z-score interpretation.



### 2. Inter-Class Equilibrium (Beta-Optimization)
To combine heterogeneous data without "scale-dominance," weights (w) are parameterized by a scale-penalty exponent (Beta):

> Weight = 1 / (Variance * Scale^Beta)

The optimal Beta (the **"Sweet Spot"**) is found by minimizing the variance of log-weights. This ensures that high-amplitude galactic data and high-precision LIGO data contribute equitably to the final metric.



### 3. Hierarchical Structure & Regularization
* **Latent Offsets:** The tool marginalizes over class-specific offsets (mu) to isolate universal scaling from instrument-specific bias.
* **Functional Regularization:** Uses **AIC/BIC** information criteria to select the optimal truncation order for the density-scaling function, preventing overfitting.

---

## Repository Contents

| File | Description |
| :--- | :--- |
| `F_cross_scale_Validation.ipynb` | **Core Suite:** Performs the Mock Data Challenge (MDC). Demonstrates ~95% signal recovery. |
| `Robustness_Analysis.ipynb` | **Stress Test:** Evaluates resilience against heavy-tailed (Student-t) noise profiles. |
| `Beta_Sensitivity_Analysis.ipynb` | **Frustration Test:** Visualizes signal decay if Beta deviates from equilibrium. |

---

## Usage

### Prerequisites
`pip install numpy scipy matplotlib`

### Running the Analysis
1. Open the .ipynb files in Jupyter or Google Colab.
2. Run the **Validation** suite first to establish the baseline Z-score.
3. Execute the **Sensitivity Analysis** to verify the Beta = 0.0015 "Sweet Spot."

---

## Citation
If you use this framework in your research, please cite the primary manuscript:
**Clinkscales, K. (2026).** *A scale-agnostic statistical test for correlated residuals in astrophysical and cosmological data.*

License:
This project is licensed under the MIT License.
