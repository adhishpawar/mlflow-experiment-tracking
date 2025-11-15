# 🚀 MLflow Model Registration & Loading 

This repository demonstrates a **minimal, clean, and
production-oriented** workflow for:

### ✅ Training a model

### ✅ Logging it to MLflow

### ✅ Registering the trained model in the MLflow Model Registry

### ✅ Loading the registered model for inference

This repo is intentionally simple and focused only on the **Model
Registry workflow**.

------------------------------------------------------------------------

# 📦 Tech Stack

-   **Python**
-   **XGBoost**
-   **scikit-learn**
-   **MLflow**
-   **Jupyter Notebook**

------------------------------------------------------------------------

# 📁 Repository Structure

    📂 mlflow-model-registry-demo
     ├── notebook.ipynb
     ├── README.md
     ├── images/
     │    ├── mlflow_registry_list.png
     │    ├── mlflow_model_version.png

------------------------------------------------------------------------

# 🔥 MLflow Workflow (Short & Clear)

Below are the *three main steps* implemented in the notebook.

------------------------------------------------------------------------

# 1️⃣ Train + Log Model (Experiment Tracking)

The notebook trains an **XGBoost Classifier**, logs:

-   parameters\
-   accuracy metric\
-   the ML model artifact

Finally, MLflow prints a **Run ID**, which you use in step 2.

📌 Code Snippet:

``` python
with mlflow.start_run() as run:
    params = {"objective": "binary:logistic", "max_depth": 4, "learning_rate": 0.1}
    model = xgb.XGBClassifier(**params)
    model.fit(X_train, y_train)

    mlflow.log_params(params)
    mlflow.log_metric("accuracy", accuracy_score(y_test, model.predict(X_test)))
    mlflow.xgboost.log_model(model, "model")

    print("Run ID:", run.info.run_id)
```

------------------------------------------------------------------------

# 2️⃣ Register the Model (Model Registry)

Using the **Run ID**, the model artifact is registered as a versioned
MLflow model.

📌 Code Snippet:

``` python
run_id = input("Enter Run ID: ")
model_uri = f"runs:/{run_id}/model"

registered_model = mlflow.register_model(
    model_uri=model_uri,
    name="XGB-Smote"
)
```

------------------------------------------------------------------------

# 3️⃣ Load Registered Model (Inference)

Once registered, you can load **any version** of the model:

📌 Code Snippet:

``` python
model_uri = "models:/XGB-Smote/1"
model = mlflow.xgboost.load_model(model_uri)

preds = model.predict(X_test)
print(preds[:5])
```

------------------------------------------------------------------------

# 📊 MLflow Model Registry UI

![Registry – Registered Models](https://raw.githubusercontent.com/adhishpawar/mlflow-experiment-tracking/main/2.%20MLFlow%20Mode%20Registry/Registry%20UI/Registered%20Models.png)

![Registry – Model Version](https://raw.githubusercontent.com/adhishpawar/mlflow-experiment-tracking/main/2.%20MLFlow%20Mode%20Registry/Registry%20UI/Model_version.png)

------------------------------------------------------------------------

# 🛠 How to Run

### Step 1: Install dependencies

``` bash
pip install mlflow scikit-learn xgboost
```

### Step 2: Launch MLflow UI

``` bash
mlflow ui
```

### Step 3: Run the notebook

Execute each cell in order.

------------------------------------------------------------------------

# 🎯 Key Takeaways

✔ MLflow tracks training runs\
✔ Artifacts can be versioned in the Registry\
✔ Registered models support lifecycle stages (Staging → Production)\
✔ Models can be loaded using `models:/name/version`\
✔ Production-grade model loading is extremely simple

------------------------------------------------------------------------

# 📌 Ideal Use Cases

-   MLOps pipelines\
-   Experiment tracking\
-   Versioned model deployments\
-   Team model collaboration\
-   Model staging → production workflows
