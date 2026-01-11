# 🚑 Ambulance Route & Hospital Optimization System

A simulation-based machine learning system that recommends optimal ambulance routing and hospital selection by balancing travel time, hospital congestion, and patient severity.

> **Disclaimer:** This project is for educational and research purposes only.  
> It does **not** use real-time EMS data, does **not** provide medical advice, and is **not intended for clinical deployment**.

---

## 📌 Problem Overview

Emergency medical routing is a multi-objective decision problem.

Routing a patient to the nearest hospital by distance alone may increase time-to-treatment if that hospital is congested. Conversely, sending a stable patient to a distant hospital may unnecessarily increase risk.

This project explores a **severity-aware decision system** that jointly optimizes:

- Estimated ambulance travel time
- Predicted emergency department wait time
- Hospital congestion risk
- Patient clinical severity

The goal is to minimize **effective treatment delay**, not just distance.

---

## 🎯 Project Scope

### Included
- Historical and simulated data only
- Machine learning models for:
  - ER wait-time prediction (XGBoost)
  - Hospital congestion risk (Random Forest)
- Severity-aware optimization logic
- Geospatial routing using road networks
- Interactive visualization of routes and decisions

### Excluded
- Real-time EMS or 911 data
- Live traffic feeds
- Clinical diagnosis or treatment decisions
- Production APIs or deployment
- Deep learning routing models

---

## 🧠 System Design

The system follows this pipeline:

1. Generate or ingest patient emergency scenarios
2. Compute travel-time estimates to candidate hospitals
3. Predict hospital wait times using machine learning
4. Estimate hospital congestion risk
5. Apply severity-aware optimization to rank hospitals
6. Visualize ambulance routes and decision rationale

---

## 📂 Data Sources

All data used is publicly available or simulated.

| Data Type | Source |
|----------|--------|
| Hospital locations | Healthsites.io (OpenStreetMap-derived) |
| Hospital capacity & utilization | HHS Hospital Capacity Dataset |
| ER wait times | Simulated ER wait-time dataset |
| Road network | OpenStreetMap (via OSMnx) |

No protected health information (PHI) is used.

---

## 🧪 Models Used

### ER Wait-Time Prediction
- **Model:** XGBoost Regressor
- **Inputs:** Time of day, day of week, hospital congestion, patient severity
- **Output:** Predicted wait time (minutes)

### Hospital Congestion Risk
- **Model:** Random Forest Classifier
- **Output:** Probability of hospital congestion

### Explainability
- SHAP values used to interpret model predictions

---

## ⚖️ Severity-Aware Optimization

Hospital selection is based on a weighted cost function:

- Higher severity → heavier penalty on wait time and congestion
- Lower severity → more flexibility in routing

This allows:
- Critical patients to avoid congested hospitals
- Stable patients to absorb slightly longer transport times

---

## 🗺️ Visualization

- Ambulance routes visualized on interactive maps
- Hospital congestion overlaid spatially
- Decisions annotated with model explanations

---

## 📊 Results (Summary)

- Severity-aware routing reduces effective treatment delay compared to nearest-hospital baseline
- Model predictions remain stable under simulated stress scenarios
- Explainable decisions improve transparency

---

## ⚠️ Limitations

- Simulated patient severity
- No real-time traffic or EMS data
- Hospital congestion approximated from historical data
- Results reflect modeling assumptions, not clinical outcomes

---

## 🛠️ Tech Stack

- Python
- Jupyter Notebook
- Pandas, NumPy
- NetworkX, OSMnx
- XGBoost, scikit-learn
- SHAP
- Folium

---

## 📌 Ethical Disclaimer

This system does **not** provide medical advice and should **not** be used for real-world emergency decision-making.

All conclusions are based on simulated scenarios and modeling assumptions.

## ⭐ Acknowledgments

- OpenStreetMap contributors
- Healthsites.io
- U.S. Department of Health & Human Services
