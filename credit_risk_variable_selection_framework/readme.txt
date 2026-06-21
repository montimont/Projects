# Credit Risk Variable Selection Framework

This project implements a credit risk variable selection and preparation framework designed to support scorecard development, model governance, and risk analytics workflows.

The framework focuses on the critical stages that occur before model training: data preparation, feature evaluation, variable selection, and smoothing. These processes are essential for building interpretable, stable, and regulator-friendly credit risk models.

## Purpose

The goal of this project is to demonstrate industry-standard techniques used to identify, evaluate, and prepare variables for credit scorecard development. The framework emphasizes interpretability, statistical rigor, and reproducible analytical workflows commonly used in lending and risk management environments.

## Components

### 1. Data Preparation

* Stratified development, validation, and holdout sampling
* Separate datasets for linear and non-linear modeling approaches
* Missing value handling and feature preparation
* Infrastructure supporting downstream scorecard development and monitoring

### 2. Feature Selection

Multiple feature evaluation techniques are implemented to assess predictive power, stability, and redundancy:

* XGBoost feature importance
* Random Forest feature importance
* Spearman correlation analysis
* Hoeffding's D dependence testing
* Logistic regression significance testing
* Variable clustering
* Weight of Evidence (WoE) analysis
* Information Value (IV) analysis

### 3. Variable Smoothing

* Variable binning and grouping
* Monotonicity enforcement
* Bad-rate smoothing
* WoE-ready variable transformation
* Preparation for interpretable scorecard development

## Techniques Covered

* Stratified sampling and data partitioning
* Feature engineering and preparation
* Statistical feature selection
* Variable clustering and redundancy reduction
* Weight of Evidence (WoE)
* Information Value (IV)
* Monotonic binning and smoothing
* Credit risk analytics best practices

## Folder Structure

credit_risk_variable_selection_framework/
│
├── 01_data_preparation/
├── 02_feature_selection/
├── 03_variable_smoothing/
│
└── README.md

## Target Audience

* Credit risk analysts
* Scorecard developers
* Quantitative researchers
* Risk analytics professionals
* Hiring managers evaluating quantitative modeling portfolios

## Project Objectives

This framework was developed to demonstrate the analytical processes that support interpretable and governance-friendly credit risk modeling. The focus is on variable preparation, statistical evaluation, and model readiness rather than predictive model deployment.

---

Built as part of a quantitative risk analytics portfolio showcasing feature selection, variable engineering, and model governance techniques commonly used in credit scoring and lending environments.
