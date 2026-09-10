# 🛒 SmartKart — Customer Churn Prediction

An end-to-end **Machine Learning project for predicting customer churn** using **Logistic Regression**.

The project takes a deliberately messy 100-customer SmartKart dataset and transforms it into a clean, model-ready dataset before building and evaluating a churn prediction model. The final output is a **business-ready customer churn risk report** that can help a retention team identify customers who may leave.

---

## 📌 Project Overview

Customer churn is a major business problem for retail companies. Identifying customers who are likely to leave allows businesses to take preventive action through better customer support, retention offers, and targeted engagement.

In this project, we use customer-level information such as:

* Age
* Monthly Spend
* Number of Complaints

to predict whether a customer is likely to **churn or stay**.

### 🎯 Business Goal

> **Predict which SmartKart customers are likely to churn so that the retention team can intervene before they leave.**

---

## 🧠 Machine Learning Approach

This project follows a complete **15-step supervised machine learning pipeline**:

1. Data Collection
2. Data Understanding
3. Data Cleaning
4. Outlier Detection & Treatment
5. Feature Selection
6. Target Variable Definition
7. Target Encoding Verification
8. Train-Test Split
9. Feature Standardisation
10. Model Building
11. Model Training
12. Prediction
13. Model Evaluation
14. Model Interpretation
15. Business-Ready Final Output

This workflow is documented directly in the project notebook.

---

## 📊 Dataset

The original dataset contains **100 customer records and 5 columns**:

| Column          | Description                                  |
| --------------- | -------------------------------------------- |
| `Customer_ID`   | Unique customer identifier                   |
| `Age`           | Customer age                                 |
| `Monthly_Spend` | Customer's monthly spending                  |
| `Complaints`    | Number of customer complaints                |
| `Churn`         | Target variable: `1 = Churn`, `0 = No Churn` |

The raw dataset intentionally contains real-world-style data quality issues including missing values, duplicate records, invalid values, inconsistent formatting, and outliers.

---

## 🧹 Data Cleaning

The raw dataset contains several data-quality problems.

### Problems identified

* Duplicate customer records
* Whitespace in customer IDs and age values
* Age stored as text
* `"thirty"` instead of `30`
* Missing values
* Invalid ages such as `-5` and `150`
* Negative monthly spending
* Extreme monthly-spend outlier
* Unrealistically high complaint count

For example, the raw dataset contains a monthly spend of `-1000`, an extreme value of `99999`, an age of `150`, and a complaints value of `50`.

### Cleaning techniques used

* Duplicate removal
* Whitespace stripping
* Data type conversion
* Invalid-value replacement
* Median imputation for missing values
* IQR-based outlier detection
* Outlier capping/winsorisation

Five duplicate rows are removed during the cleaning process, reducing the dataset from 100 to 95 records.

---

## 🔍 Features & Target

### Features

The model uses three business-relevant features:

```text
Age
Monthly_Spend
Complaints
```

`Customer_ID` is excluded because it is an identifier rather than a meaningful predictive feature.

### Target

```text
Churn
```

where:

```text
0 → No Churn
1 → Churn
```

The target is already numeric, so additional encoding is not required.

---

## ⚙️ Model

### Logistic Regression

**Algorithm:** Logistic Regression

Logistic Regression was selected because churn is a **binary classification problem**. It also provides churn probabilities, which can be used to rank customers according to their risk level.

### Train-Test Split

The dataset is divided into:

* **80% Training Data**
* **20% Testing Data**
* `random_state = 42`
* Stratified splitting to maintain the churn distribution

The notebook reports 76 customers for training and 19 for testing after cleaning.

### Feature Scaling

`StandardScaler` is used to standardise the numerical features.

The scaler is fitted only on the training data and then applied to the test data to avoid data leakage.

---

## 📈 Model Evaluation

The model is evaluated using:

* **Confusion Matrix**
* **Accuracy**
* **Precision**
* **Recall**
* **F1-Score**
* Classification Report

The notebook's documented expected evaluation is approximately:

| Metric    | Approximate Result |
| --------- | -----------------: |
| Accuracy  |             89–95% |
| Precision |             83–91% |
| Recall    |              ~100% |
| F1-Score  |               High |

These values should be treated as the notebook's documented approximate results; rerunning the notebook is recommended for the exact metrics generated in your environment.

---

## 💡 Business Insights

The Logistic Regression coefficients are used to understand which factors are associated with churn.

### Key findings

**1. Complaints → Higher churn risk**

A higher number of complaints is associated with increased churn risk.

This makes customer-support and complaint resolution an important retention lever.

**2. Monthly Spend → Lower churn risk**

Higher monthly spending is associated with lower churn risk in this dataset.

High-spending customers therefore represent an important customer segment to protect.

**3. Age → Smaller effect**

Age has a comparatively weaker effect on churn than Monthly Spend and Complaints.

The notebook's main business takeaway is:

> **Reducing customer complaints and protecting high-spend customer relationships are two important retention levers for SmartKart.**

---

## 🎯 Final Business Output

Instead of stopping at model accuracy, the project converts predictions into an actionable **Customer Churn Risk Report**.

The report contains:

* Customer ID
* Age
* Monthly Spend
* Complaints
* Actual Churn
* Predicted Churn
* Churn Probability
* Risk Label

Customers are ranked according to their predicted churn probability, allowing the retention team to prioritise the highest-risk customers first.

### Risk Labels

```text
Likely to Churn
Not Likely to Churn
```

The notebook also identifies the **top 5 highest-risk customers** for immediate retention attention.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **Jupyter Notebook / Google Colab**

---

## 📁 Project Structure

```text
smartkart-customer-churn-prediction/
│
├── SmartKart_Churn_Prediction_ML_Pipeline.ipynb
├── SmartKart_dirty_100_rows.csv
├── smartkart_churn_risk_report.csv
└── README.md
```

---

## 🚀 How to Run

### Option 1 — Google Colab

1. Open the `.ipynb` notebook in Google Colab.
2. Upload `SmartKart_dirty_100_rows.csv`.
3. Run the notebook from top to bottom.
4. Review the data-cleaning process.
5. Review the model evaluation metrics.
6. View the final churn risk report.

The notebook is designed to be executed sequentially from the first cell to the final output.

### Option 2 — Jupyter Notebook

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Then launch:

```bash
jupyter notebook
```

Open:

```text
SmartKart_Churn_Prediction_ML_Pipeline.ipynb
```

and run all cells.

---

## 📌 Project Highlights

* ✅ Complete end-to-end ML pipeline
* ✅ Real-world-style messy dataset
* ✅ Data cleaning and preprocessing
* ✅ Missing-value handling
* ✅ Duplicate removal
* ✅ Outlier treatment using IQR
* ✅ Feature selection
* ✅ Feature standardisation
* ✅ Logistic Regression classification
* ✅ Confusion matrix
* ✅ Accuracy, Precision, Recall and F1 evaluation
* ✅ Model coefficient interpretation
* ✅ Churn probability prediction
* ✅ Business-ready risk report

---

## 💼 Business Application

A real retail company could integrate a similar system into its customer-retention workflow.

For example:

```text
Customer Data
     ↓
Data Cleaning
     ↓
ML Model
     ↓
Churn Probability
     ↓
Risk Ranking
     ↓
Retention Action
```

High-risk customers could then be prioritised for:

* Customer-support follow-ups
* Retention offers
* Personalised communication
* Complaint resolution
* Loyalty initiatives

---

## 📚 Learning Outcomes

This project demonstrates practical understanding of:

* Supervised Machine Learning
* Binary Classification
* Data Preprocessing
* Feature Selection
* Outlier Detection
* Missing-Value Treatment
* Standardisation
* Logistic Regression
* Model Evaluation
* Model Interpretation
* Business-oriented ML

---

## 👤 Author

**Arshdeep Verma**

BBA FinTech & AI Student
Interested in **Finance, AI, Business Analytics & Strategy**

---

⭐ If you found this project useful, consider giving the repository a star!
