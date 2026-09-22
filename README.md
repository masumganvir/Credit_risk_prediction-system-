# Credit Risk Assessment using SHAP

![Credit Ledger Logo](static/logo.jpg)

**Credit Ledger** is a machine learning-powered web application for assessing consumer loan applications. It predicts the default probability of a loan applicant using an XGBoost model, evaluated with SHAP (SHapley Additive exPlanations) for interpretability, and presents the decision through a highly interactive, glassmorphism-styled modern web interface.

---

## 👨‍💻 Author
**Masum Ganvir**

---

## 🚀 Features
- **Machine Learning Backend:** Uses a pre-trained XGBoost model to evaluate loan risk (High Risk vs Low Risk).
- **FastAPI Server:** Provides a blazing fast RESTful API endpoint (`/predict`) to serve the model predictions.
- **CORS Enabled:** The API can be securely consumed from cross-origin frontend deployments.
- **Modern Glassmorphism UI:** Features a sleek, dark-themed, glass-like interface with glowing neon animations, smooth transitions, responsive grid layouts, and dynamic risk gauges.
- **Interactive Verdict:** Upon submission, the UI provides an animated gauge reading, a stamped verdict (LOW RISK / HIGH RISK), and clear decision metrics.

---

## 🛠️ Technology Stack
- **Backend:** Python 3.12+, FastAPI, Uvicorn, Pydantic V2, Scikit-Learn, Pandas, XGBoost, Joblib.
- **Frontend:** HTML5, Vanilla JavaScript, CSS3 (CSS Grid, CSS Variables, Glassmorphism).

---

## ⚙️ Installation & Local Setup

### 1. Clone the repository
Ensure you have the project files locally on your machine.

### 2. Install dependencies
It is recommended to use a virtual environment. Install the required Python packages using:
```bash
pip install -r requirements.txt
```

### 3. Run the application
Start the FastAPI server via Uvicorn:
```bash
python -m uvicorn main:app --reload
```
*Note: By default, the application will run on `http://127.0.0.1:8000`.*

### 4. Access the App
Open your web browser and navigate to `http://127.0.0.1:8000`. The frontend is served directly by FastAPI.

---

## 📡 API Reference

### `POST /predict`
Evaluates a loan applicant.

**Request Body (JSON):**
```json
{
  "person_age": 30,
  "person_income": 600000.0,
  "person_home_ownership": "MORTGAGE",
  "person_emp_length": 5.0,
  "loan_intent": "EDUCATION",
  "loan_grade": "A",
  "loan_amnt": 100000.0,
  "loan_int_rate": 11.5,
  "loan_percent_income": 0.17,
  "cb_person_default_on_file": "N",
  "cb_person_cred_hist_length": 6
}
```

**Response (JSON):**
```json
{
  "default_probability": 0.025281036688612167,
  "default_prediction": 0,
  "threshold": 0.9996131062507629,
  "Result": "Low Risk"
}
```

---

## 🌐 Deployment
The codebase is structured to be easily deployed to modern PaaS providers. 

- **Frontend & Backend together:** Since the frontend is mounted as static files in `main.py`, deploying the FastAPI app (e.g., on Render, Railway, or Heroku) will host both the UI and the API.
- **Decoupled Architecture:** If you choose to host the `static/` files on a CDN (like Vercel or Netlify) and the FastAPI backend on a separate server, the API is already configured with **CORS** (`allow_origins=["*"]`) to seamlessly permit cross-origin requests.

---

*Figures and probabilities are model estimates, not a definitive lending decision. Recorded for reference only.*
