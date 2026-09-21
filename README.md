# 📦 Brazilian E-Commerce AI Prediction System

An end-to-end Machine Learning prediction system built with **Python for both backend and frontend**, utilizing the **Olist Brazilian E-Commerce Dataset** downloaded automatically via `kagglehub`.

---

## 🔗 Dataset Link
- **Dataset:** [Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Dataset Handle:** `olistbr/brazilian-ecommerce`

---

## 📖 Project Description

In large-scale e-commerce, accurate logistics forecasting and proactive delay management directly determine customer retention, review sentiment, and operational costs. This project builds a multi-task predictive machine learning engine on over **96,400 real-world commercial orders** from Brazil's leading marketplace (Olist), providing real-time predictions for:

1. **Delivery Duration (Days)**: Machine learning regression forecasting transit duration from purchase date to doorstep delivery.
2. **Late Delivery Risk Probability**: Binary classification model estimating the risk of an order arriving past the promised Service Level Agreement (SLA) deadline.
3. **Customer Satisfaction (Review Score 1–5)**: Sentiment forecasting model factoring in transit speed, delay gap, freight share, and physical parcel attributes.

The project features a **Python FastAPI backend** with RESTful endpoints alongside **two interactive frontends**:
- A **Streamlit Python Application** (`app_streamlit.py`) written 100% in Python.
- A **Modern Glassmorphic Web Dashboard** (`backend/static/`) served directly by FastAPI.

---

## 💻 Technologies Used

| Layer | Technologies |
| :--- | :--- |
| **Language & Environment** | Python 3.11+ |
| **Data Acquisition** | `kagglehub` |
| **Data Manipulation** | `pandas`, `numpy` |
| **Machine Learning** | `scikit-learn` (`HistGradientBoostingRegressor`, `HistGradientBoostingClassifier`), `joblib` |
| **Backend & API** | `FastAPI`, `Uvicorn`, `Pydantic` |
| **Python Frontend** | `Streamlit`, `Plotly` |
| **Web Dashboard** | HTML5, Vanilla CSS3 (Glassmorphism), JavaScript (ES6) |
| **Testing & Documentation** | `pytest`, `python-docx` |

---

## 📁 Project Submission Files

| Required Item | File Name | Description |
| :--- | :--- | :--- |
| **Code File (.ipynb)** | `Salman_BrazilianEcommercePrediction.ipynb`<br>*(also available as `YourName_ProjectName.ipynb`)* | Complete self-contained Jupyter Notebook covering data download, cleaning, EDA, feature engineering, model training, evaluation, and inference. |
| **Requirements File** | `requirements.txt` | Complete list of required Python libraries and dependencies. |
| **Project Report (.docx)** | `Salman_ProjectReport.docx`<br>*(also available as `YourName_ProjectReport.docx`)* | Comprehensive project documentation in Microsoft Word format, including executive summary, problem statement, methodology, model benchmark tables, and business implications. |
| **README File** | `README.md` | Project overview, dataset link, setup/run instructions, and key information. |

---

## ⚙️ Setup & Run Instructions

### 1. Clone/Open the Workspace & Install Dependencies
```powershell
pip install -r requirements.txt
```

### 2. Download Dataset & Train Models (Automated)
Run the data pipeline to download the dataset via `kagglehub` and preprocess the features:
```powershell
python data_pipeline.py
```
Train and serialize all three machine learning models:
```powershell
python train_models.py
```

### 3. Launch the Application

#### Option A: FastAPI Backend + Modern Web Dashboard
```powershell
python run_app.py
```
- Open **[http://localhost:8000](http://localhost:8000)** in your browser for the web UI.
- Interactive Swagger API docs: **[http://localhost:8000/docs](http://localhost:8000/docs)**.

#### Option B: Streamlit Python Frontend
```powershell
python run_app.py --streamlit
# Or: streamlit run app_streamlit.py
```
- Open **[http://localhost:8501](http://localhost:8501)** in your browser for the pure Python dashboard.

#### Option C: Launch Both Simultaneously
```powershell
python run_app.py --all
```

### 4. Run Automated Tests
```powershell
pytest backend/test_api.py -v
```

---

## 📊 Model Performance Benchmarks

| Model | Target | Algorithm | Performance Metrics |
| :--- | :--- | :--- | :--- |
| **Delivery Duration** | `delivery_days` (Days) | `HistGradientBoostingRegressor` | **MAE: 4.62 days** \| RMSE: 7.11 days \| $R^2$: 0.370 |
| **Late Delivery Risk** | `is_late` (Binary) | `HistGradientBoostingClassifier` | **ROC-AUC: 0.776** \| Accuracy: 75.2% |
| **Customer Satisfaction** | `review_score` (1–5) | `HistGradientBoostingRegressor` | **MAE: 0.97 stars** \| RMSE: 1.25 |

---

## 🔑 Key Features & Highlights

- **1-Click Historical Presets**: Test real orders (Fast Local Delivery, Interstate Route, Heavy Freight Cargo, High Delay Risk).
- **What-If Logistics Simulator**: Interactively test the effect of changing fulfillment centers, freight pricing, or parcel weight.
- **Logistics Factor Explainability**: Instant breakdown of delay drivers (intra-state vs interstate transit, cargo weight penalties, SLA buffer safety, freight spend burden).
- **Production-Ready REST API**: Fully typed Pydantic request/response schemas with health checks and CORS support.
