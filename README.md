# BiqDS: Biophysics-Informed Quantitative Diabetes Screener

This project develops a fully interpretable, biologically grounded diabetes risk screener using structured signal logic and hybrid probabilistic gating. Unlike black-box models, this system prioritizes high recall, transparency, and modular reasoning — ideal for real-world healthcare screening and research environments.

---

## 🧠 Key Concept

**BiqDS** (Biophysics-Informed Quantitative Diabetes Screener) is based on the insight that:
> _Early onset of diabetes is associated with a measurable reduction in projected longevity within phenotypic clusters._

Using this principle, the system builds a `FinalSignal` that blends:
- Cluster-level longevity estimates,
- Observed diabetes prevalence,
- Delta in life expectancy between diabetic and non-diabetic patients,
- And hybrid filters using Random Forest model confidence when needed.

---

## 🚀 Features

- ✅ **Unsupervised phenotypic clustering** (`k=35`) to define biological groupings
- ✅ **Longevity modeling** from cluster-level age averages
- ✅ **Δ-longevity weights** to adjust signal confidence
- ✅ **FinalSignal**: interpretable risk score derived from biophysical and statistical logic
- ✅ **Threshold sweep** and F1 optimization
- ✅ **Hybrid filtering** with Random Forest probability for robust screening
- ✅ **High recall configuration** for maximum sensitivity

---

## 📊 Methodology Overview

1. **Data Cleaning & Clipping**  
   Remove impossible values and apply domain-informed outlier clipping to enhance medical validity.

2. **Clustering (KMeans)**  
   Segment patients into biological phenotype clusters using scaled input features.

3. **Longevity Modeling**  
   Compute average age per cluster and normalize to build a `LongevityScore`.

4. **Diabetes Prevalence**  
   Measure cluster-level diabetes probability.

5. **Delta-Longevity Weighting**  
   Estimate how much diabetes shortens life within each cluster to compute `DeltaLongevityWeight`.

6. **FinalSignal Construction**  
   Blend `LongevityScore` and `DiabetesProbability` with `DeltaLongevityWeight`.

7. **Threshold Optimization**  
   Sweep fixed thresholds (e.g. 0.10–0.25) to select high-recall, high-F1 configurations.

8. **Hybrid Rule (Optional)**  
   Apply a probability veto using a Random Forest trained on correlation-ranked features.

---

## 📈 Example Output

| Threshold | Accuracy | Precision | Recall | F1 Score |
|-----------|----------|-----------|--------|----------|
| 0.20      | 0.85     | 0.68      | 0.88   | 0.77     |
| 0.10 (high recall) | 0.77 | 0.53 | 0.98 | 0.69 |

Confusion matrix and classification reports included in the notebook.

---

## 🧪 How to Run

1. Clone the repo  
   ```bash
   git clone https://github.com/yourusername/biqds-diabetes-screener
   cd biqds-diabetes-screener

   Run the notebook:
BiqDS.ipynb

Dataset required:
Place diabetes.csv (PIMA dataset) in the same directory.


