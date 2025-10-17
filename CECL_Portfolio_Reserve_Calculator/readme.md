
# CECL Portfolio Reserve Calculator

An interactive, browser-based **Current Expected Credit Loss (CECL)** calculator built in **vanilla JavaScript** compliant with **ASC 326** standards and designed to showcase practical credit risk analytics.

This tool allows users to model **lifetime expected credit losses** using:
- Portfolio segmentation (e.g., Mortgage, Auto, Commercial)
- Probability of Default (PD) and Loss Given Default (LGD) inputs
- Scenario analysis (Base, Adverse, Severe)
- Prepayment and discount rate adjustments
- Dynamic PD curve editing
- Full visualization of reserve build-up and expected losses over time

---

## **See It in Action**

👉 **[Live Demo on GitHub Pages](https://montimont.github.io/Projects/CECL_Portfolio_Reserve_Calculator/cecl_calc.html)**

The app runs entirely in the browser — no dependencies, no backend required.

---

## **Features**

✅ **CECL-Compliant Reserve Calculation**
- Computes expected lifetime credit losses with conditional (marginal) PDs  
- Discounts expected losses using monthly discount factors  
- Supports constant prepayment and amortization assumptions  

✅ **Portfolio Segmentation**
- Three hard-coded segments (Mortgage, Auto Loans, Commercial)  
- Each with configurable PD/LGD/maturity parameters  

✅ **Dynamic PD Curve**
- Add or remove PD curve points per segment  
- Automatic linear interpolation between months  

✅ **Scenario & Sensitivity Analysis**
- Base, Adverse, and Severe macro scenarios  
- Visual reserve sensitivity chart  

✅ **Vintage Comparison**
- Compare 2023 vs. 2024 originations in reserve trajectory  

✅ **Export & Audit**
- One-click export to CSV  
- Methodology notes and assumptions included for transparency  

✅ **Dark Mode**
- Toggle for improved readability and presentation  

---

## **Formulas & Methodology**

**Reserve Formula:**
\[
\text{CECL Reserve} = \sum (EAD_t × \text{Marginal PD}_t × LGD × DF_t)
\]

**Definitions:**
- **EAD:** Exposure at Default  
- **PD:** Marginal Probability of Default (conditional on survival)  
- **LGD:** Loss Given Default  
- **DF:** Discount Factor  

Assumptions:
- Linear PD interpolation between curve points  
- Constant prepayment rate (monthly)  
- Monthly compounding discount rate  
- Lifetime expected losses consistent with ASC 326  

---

## **Usage**

1. Clone or download this repository.  
2. Open `cecl_calc.html` in any modern browser.  
3. Adjust inputs or use the **📂 Load Sample Portfolio** button.  
4. Click **Calculate Portfolio CECL** to view results, charts, and exports.

---

## 📎 **File Structure**

/Projects/CECL_Portfolio_Reserve_Calculator/
│
├── cecl_calc.html ← Full interactive calculator
└── README.md ← This documentation file


---

## **About**

Built as part of a credit risk analytics portfolio to demonstrate:
- CECL methodology implementation  
- Quantitative model transparency  
- Practical JavaScript data visualization  
