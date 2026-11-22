# 🛡️ Real-Time Credit Card Fraud Detection & Risk Scoring Engine

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.3+-green.svg)
![ML Models](https://img.shields.io/badge/ML%20Models-8-orange.svg)
![PWA](https://img.shields.io/badge/PWA-Enabled-purple.svg)

*An end-to-end machine learning risk scoring engine and progressive web dashboard for real-time transaction fraud detection, anomaly analysis, and ensemble evaluation.*

[Report Bug](https://github.com/ummeazra0345/Credit-Card-Fraud-Detection-System/issues) • [Request Feature](https://github.com/ummeazra0345/Credit-Card-Fraud-Detection-System/issues)

</div>

---

## 🔍 Overview

Financial fraud detection requires balancing two competing operational priorities: **catching emerging fraudulent patterns (High Recall)** while **minimizing false declines for legitimate customers (High Precision)**. 

This project implements a low-latency fraud risk scoring system powered by 8 supervised and ensemble machine learning classifiers alongside a Progressive Web Application (PWA) dashboard. It enables risk analysts and data scientists to score transactions in real time (<500ms), run multi-model ensemble comparisons, inspect feature correlations, and evaluate classification thresholds on heavily imbalanced transaction datasets.

---

## ✨ Key Capabilities

### 🤖 Fraud Modeling & Risk Scoring
- **8 Classification & Ensemble Architectures**: Logistic Regression, Support Vector Machine (SVM), K-Nearest Neighbors (KNN), Decision Tree, Random Forest, Gradient Boosting, XGBoost, and AdaBoost.
- **Multi-Strategy Inference**: Supports single-model scoring, unweighted ensemble voting, accuracy-weighted scoring, and sequential cascade thresholding.
- **Imbalanced Class Optimization**: Incorporates specialized sampling and balanced tree architectures (Balanced Random Forest, Easy Ensemble) to address extreme class skew typical of payment ecosystems.
- **Low-Latency Scoring**: Delivers inference responses in under 500ms via lightweight REST endpoints.

### 📊 Risk Analytics & Diagnostics
- **Feature Attribution & Correlation**: Evaluates 29 PCA-transformed and transactional features (`V1`–`V28`, `Amount`) to surface top fraud indicators.
- **Transaction Amount Profiling**: Compares spending distributions and temporal anomalies between legitimate and fraudulent cohorts.
- **Model Evaluation Suite**: Tracks Precision, Recall, F1-Score, ROC curves, and overall classification accuracy across test batches.

### 🌐 Interactive Web Dashboard & PWA
- **Batch & Single-Transaction Scoring**: Upload CSV transaction logs for bulk evaluation or test individual feature vectors via the web UI.
- **Progressive Web App (PWA)**: Installable on mobile and desktop with Service Worker caching for offline documentation and queued scoring.
- **Interactive Visualizations**: Built with Plotly.js and Chart.js for dynamic drill-downs into class distributions and model trade-offs.

---

## 🛠️ Tech Stack

| Layer | Technologies |
| :--- | :--- |
| **Machine Learning & Data** | Python 3.8+, Scikit-Learn, XGBoost, Imbalanced-Learn, Pandas, NumPy |
| **Backend & API** | Flask 2.3+, Werkzeug, RESTful JSON APIs, Pickle / XGBoost JSON Serialization |
| **Frontend & Visualization** | HTML5, CSS3, JavaScript (ES6+), Plotly.js, Chart.js |
| **PWA & Deployment** | Service Workers, Web App Manifest, Docker, Gunicorn / Railway |

---

## 📁 Repository Architecture

```text
Credit-Card-Fraud-Detection-System/
├── app.py                          # Main Flask server & inference API endpoints
├── save_model.py                   # Model training, evaluation & serialization pipeline
├── requirements.txt                # Python dependencies
├── railway.toml                    # Cloud deployment configuration
├── Procfile                        # WSGI process declaration
├── runtime.txt                     # Python runtime specification
├── templates/                      # Frontend views (Dashboard, Models, Analytics, Theory)
│   ├── index.html                  # Main dashboard & batch CSV upload
│   ├── model.html                  # Real-time transaction scoring interface
│   ├── visualizations.html         # Interactive fraud distribution charts
│   ├── analysis.html               # Statistical & model comparison metrics
│   ├── feature.html                # Feature importance & correlation breakdown
│   ├── amount-trends.html          # Transaction amount & temporal behavior
│   ├── theory.html                 # Mathematical & algorithmic documentation
│   └── offline.html                # PWA offline fallback view
├── static/                         # CSS, client-side JS, Service Worker & PWA manifest
├── ml model/                       # Serialized model artifacts (.pkl & xgb_model.json)
└── dataset/                        # Holdout evaluation dataset (test-2.csv)
