
# MLflow Setup & End-to-End Testing (with 3 Notebooks)

This README explains:

- **Why we need MLflow (Real-life explanation)**
- **What is MLflow**
- **MLflow Components**
- **Setup using Git Bash + Anaconda Notebook**
- **Data flow from Notebook → MLflow**
- **Explanation of the 3 test notebooks**
- **Images of MLflow UI**
---

## 🧠 Why Do We Need MLflow? (Real-Life Explanation)

In real-life ML engineering:

- You train **multiple models** with different parameters.
- You need to track **which model performed best**.
- You want to **reproduce old experiments** anytime.
- You want to **compare models** visually.
- You need a place to **store models**, versions, artifacts.
- Your model needs to be deployed with **full version control**.

MLflow solves all of this.

---

## 🚀 What Is MLflow?

MLflow is an **open-source Machine Learning Lifecycle Management platform**.

It helps you with:

- **Experiment Tracking**
- **Model Management & Versioning**
- **Model Deployment**
- **Artifacts Storage**

---

## 🧩 MLflow Components (Very Simple Explanation)

| Component | Purpose |
|----------|----------|
| **MLflow Tracking** | Tracks parameters, metrics, runs, artifacts |
| **MLflow Projects** | Packaging reproducible ML code |
| **MLflow Models** | Standard format to save models |
| **Model Registry** | Central place to version, stage, approve models |

---

## 🛠️ Setup: Git Bash + Conda + Notebook

### **1. Create Conda Environment**
```bash
conda create -n mlflow-demo python=3.10 -y
conda activate mlflow-demo
```

### **2. Install MLflow**
```bash
pip install mlflow scikit-learn pandas matplotlib
```

### **3. Run MLflow UI**
```bash
mlflow ui
```

Then open:
```
http://127.0.0.1:5000
```

---

## 🔄 Data Flow: Notebook → MLflow

```
Your Notebook
   │
   ├─→ log_params()     → Saves model parameters
   ├─→ log_metrics()    → Saves accuracy, loss, etc.
   ├─→ log_artifact()   → Saves images, JSON, files
   └─→ log_model()      → Saves the ML model 

MLflow Server
   │
   └─→ UI Visualization + Compare + Registry
```

---

## 📘 Explanation of the 3 Notebooks

### **Notebook 1 — Basic Logging & Metrics**
Tracks:
- Parameters (auto-logged)
- Metrics like accuracy / MSE
- Model artifacts

This verifies **tracking + UI logging works**.

---

### **Notebook 2 — Custom Artifacts & Parameters**
You manually store:
- Custom parameters
- Manually logged metrics
- JSON files or any artifacts

This tests **artifact storage**.

---

### **Notebook 3 — Model Registry**
You:
- Train a model
- Log it
- Register it in the Model Registry
- Load it back

This tests:
- **Model Versioning**
- **Registry**
- **Model loading API**

---

## 📸 MLflow UI Screenshots

### Experiments View
![MLflow UI](New%20folder/MLFlow%20UI%20(4).png)
![MLflow UI](New%20folder/MLFlow%20UI%20(5).png)
![MLflow UI](New%20folder/MLFlow%20UI%20(1).png)

---

## ✅ You're Ready!

You now have:
- Full understanding of MLflow
- 3 working notebooks
- Model tracking + artifacts + registry
- A clean MLflow setup for real ML engineering

---
