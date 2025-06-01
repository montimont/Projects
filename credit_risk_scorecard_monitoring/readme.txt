# Credit Risk Monitoring System – Portfolio Project

This project demonstrates a **credit risk monitoring framework** built in Python, focused on tracking the stability and performance of a simplified internal credit score over time.

## Project Goal

To simulate how financial institutions monitor the **health and reliability of credit scoring models** using statistical and visual tools, even in the absence of production infrastructure or real-time data streams.

The focus is on **model monitoring**, not on production-ready modeling or scorecard optimization.

---

##  Key Components

### 1. **Internal Credit Score Simulation**
- A simplified **logistic regression model** is trained on development data.
- The output is transformed into an **internal credit score** scaled similarly to a FICO range (300–850).
- `age` is excluded to reflect regulatory sensitivity (e.g., ECOA compliance).

### 2. **Monitoring Metrics Implemented**
- **PSI (Population Stability Index)**: Measures score distribution shifts over time.
- **CSI (Characteristic Stability Index)**: Detects feature-level data drift using score differences.
- **KDE Plots**: Visual comparisons of score and feature distributions across time.

### 3. **Interpretation & Reporting**
- Includes Markdown-based narrative summaries explaining:
  - How PSI and CSI work
  - What stability thresholds mean
  - Recommendations based on findings

---

Note: This project does not include Gini or KS metrics, as the primary focus is not on model performance optimization but on simulating a scorecard for stability monitoring.


