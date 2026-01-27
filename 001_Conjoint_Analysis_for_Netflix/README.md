# Choice-Based Conjoint Analysis – Netflix Survey

## Project Overview
This project implements a **Choice-Based Conjoint Analysis (CBC)** using Python to quantify customer preferences based on survey data.  
The analysis is built around a **binary choice model** and focuses on estimating **part-worth utilities** and **attribute importance** using statistical modeling techniques.

The project is designed as a **portfolio-ready data analytics case**, simulating a real-world market research scenario for a global streaming platform.

---

## Objectives
- Estimate customer preferences across multiple product attributes
- Identify statistically significant attribute levels
- Quantify the relative importance of each attribute
- Explore interaction effects between selected attributes

---

## Methodology
- One-hot encoding of conjoint attribute levels
- **Generalized Linear Model (GLM)** with **Binomial family (logistic regression)**
- Extraction of part-worth utilities and p-values
- Calculation of attribute importance using the utility range method
- Visualization of results for interpretability

---

## Key Features
- Part-worth utility estimation using **Statsmodels**
- Attribute importance normalization to 100%
- Visual analytics (bar charts, treemap)
- Interaction term analysis (content × ads)

---

## Tools & Technologies
- Python  
- Pandas  
- NumPy  
- Statsmodels  
- Matplotlib  
- Squarify  

---

## Output
- Estimated preference utilities for each attribute level
- Relative importance of features driving customer choice
- Visual summaries supporting analytical interpretation

---

## Notes
This project focuses strictly on **analytical modeling and interpretation** and does not include production deployment or automated pipelines.  
It is intended as a **demonstration of applied data analysis and market research skills**.

