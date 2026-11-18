# BST260 Final Project Proposal

**To: BST260 Teaching Team, Fall 2026**

## 1. Project Overview

This project will analyze two public health datasets using statistical
methods introduced in BST260: NHANES and CDC waterborne illness data.
The first analysis will focus on age-specific health outcomes (NHANES
Option 1) and incorporate spline regression from Option 2. The second
will compare statistical models for outbreak count data. Both analyses
will be presented as reproducible Quarto vignettes in the `finalproject`
R package.

## 2. Analysis 1: NHANES — BMI and Blood Pressure

### Research Question

Among U.S. adults aged 40 and older, how is BMI associated with systolic
blood pressure, and does spline regression improve model fit compared
with linear regression?

### Variables and Study Population

- **Population and unit:** NHANES participants aged 40+, with each
  participant representing one observation.
- **Exposure:** BMI (kg/m²), modeled continuously and categorized for
  descriptive analysis.
- **Outcome:** Average systolic blood pressure (`BPSysAve`), a
  continuous variable measured in mmHg.
- **Confounders:** Age, sex, race/ethnicity, and smoking status,
  selected based on subject-matter considerations.
- **Missing data:** Examine missingness and use complete-case analysis
  as the primary approach.

### Planned Statistical Analysis

I will summarize participant characteristics and visualize BMI and blood
pressure distributions. Adjusted linear regression will estimate the
association between BMI and systolic blood pressure. Natural cubic
spline regression using
[`splines::ns()`](https://rdrr.io/r/splines/ns.html) will assess
potential nonlinear relationships.

Models will be compared using AIC, fitted curves, and residual
diagnostics. I will also explore BMI-by-sex interactions and consider
survey weights if suitable design information is available.

## 3. Analysis 2: CDC Waterborne Illness — Count Regression

### Research Question

How does water system type relate to the number of illnesses per
reported outbreak, and does negative binomial regression provide a
better fit than Poisson regression?

### Variables and Study Population

- **Population and unit:** Reported U.S. waterborne disease outbreaks,
  with each outbreak representing one observation.
- **Exposure:** Water system type (`water_type`), comparing community
  and individual/private systems.
- **Outcome:** Number of reported illnesses (`illnesses`), a nonnegative
  count variable.
- **Confounders:** Calendar period and geographic region, with etiology
  considered in secondary analyses.
- **Missing data:** Convert the list-based dataset into a tidy data
  frame, examine missing values, and exclude incomplete records from the
  primary analysis.

### Planned Statistical Analysis

I will summarize outbreak frequencies and illness counts by water system
type, region, and year. Visualizations will include distributions of
outbreak sizes and temporal trends.

I will fit Poisson and negative binomial regression models and compare
AIC, dispersion statistics, residual diagnostics, and estimated
associations. Sensitivity analyses will assess the influence of
unusually large outbreaks.

## 4. Reproducibility and Limitations

The project will include two analysis vignettes:

- `nhanes_analysis.qmd`: BMI and systolic blood pressure using linear
  and spline regression.
- `waterborne_analysis.qmd`: Waterborne outbreak counts using Poisson
  and negative binomial regression.

Both analyses will document data provenance, descriptive statistics,
visualizations, reusable R functions, statistical findings, and
limitations.

Potential limitations include missing data, residual confounding, NHANES
survey design, and incomplete outbreak reporting. Results will be
interpreted as observational associations rather than causal effects.

The completed project will be published through the `finalproject`
pkgdown website on GitHub Pages.
